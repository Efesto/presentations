## When Elixir met Kloeckner.I...



When Elixir met Klockner.I, KCI had already a programming language...



### Ruby is...

_A dynamic, open source programming language with a focus on simplicity and productivity. It has an elegant syntax that is natural to read and easy to write. - https://www.ruby-lang.org/_



```Ruby
cities  = %w[London Oslo Paris Amsterdam Berlin]
visited = %w[Berlin Oslo]

puts "I still need to visit" + 
"the following cities:", cities - visited
```
 
```Bash
> I still need to visit the following cities:
London
Paris
Amsterdam
```



* Ruby is considered an excellent language by many and its characteristics make it allow its developers to be productive and "happy".
* Is behind many successful products like Shopify, Github and [Gitlab](https://about.gitlab.com/blog/2018/10/29/why-we-use-rails-to-build-gitlab/).



...and what about Elixir?...



* It's a modern language that combines the syntax and the philosophy of Ruby with the power of Erlang.
* Tested in KCI for developing supporting tools in the KMC stack.
* Became the starting point for a new user facing tool called Kloeckner Assistant.

Note: the fact that Elixir is looking similar to Ruby is the reason for which many Elixir developers have Ruby experience, also at KCI



### Elixir is...
_Elixir is a dynamic, functional language for building scalable and maintainable applications. - https://elixir-lang.org/_

Note:
Created by Jose' Valim, one of the top contributors to Ruby on Rails.
Open source and community driven.



```Elixir
defmodule Fibonacci do 
  def fib(0), do: 0
  def fib(1), do: 1
  def fib(n), do: fib(n-1) + fib(n-2)
end

IO.puts(Fibonacci.fib(15))
```

```Bash
> 610
```

Note: Let's try to disassemble the previous statement for understanding what we are talking about



> "Elixir is a functional language"

* Adopts a functional paradigm, which involves immutable data.
* Practically means less complexity and less "side effects" compared to other commonly used paradigms.
* One of the main differences with Ruby in terms of usability.​

Note: Being functional is one of the characteristics that differentiates Elixir from Ruby (doesn't mean that "it functions")
I'll not go in the topic of comparing the different programming language paradigms in this presentation.
So please take this assertion "functional means less complexity" as it is for the sake of simplicity



> "Elixir is for building scalable and maintainable applications"

* Elixir is built on top of Erlang.
* Erlang is a programming language built by Ericsson and released in 1986 for developing distributed systems.

Note: The original purpose of Erlang was for developing systems that have to fullfill high reliability requirements, specifically telephone switches
We are literally building on giants' shoulders



_Erlang is used to build massively scalable soft real-time systems with requirements on high availability_ - https://www.erlang.org/



In 2023, Erlang and Elixir are battle-tested tools:
* [WhatsApp](https://www.erlang-solutions.com/blog/20-years-of-open-source-erlang-openerlang-interview-with-anton-lavrik-from-whatsapp/)
* [Cisco](https://codesync.global/media/https-youtu-be-077-xjv6plq/) for its routers
* [Discord](https://discord.com/blog/how-discord-scaled-elixir-to-5-000-000-concurrent-users)



## How Kloeckner Assistant uses Elixir?

* Web stack
* Email processing
* ERP communication
* Metadata Platform - Match!, Ingestion, Search, Exporter



## for doing more faster

* Email and dataset processing are tasks that require processing a big amount of information in the shortest time possible.
* This needs to be done without influencing the perfomance of the web stack.
* Elixir's scalability allowed us to solve such problem without the need of complex architectures or proprietary tools.



* Over 1.200.000 Emails received and processed by Assistant.
* Over 1.200.000 Datasets imported by Metadata Platform Ingestion.



## for doing more with clarity

* Matching machine implements complex algorithms for suggesting the closest material as possible given an order entry.
* The simplicity and expressiveness of Elixir allowed us to scale up the complexity while maintaining the code understandable.




```Elixir
@decorate trace()
def get(%Request{} = req) do
  {exact_matches, predictions} =
    req
    |> find_exact_matches_and_predictions()
    |> @metadata.preload_matches()
    |> @metadata.preload_materials(req.organization_code, req.subsidiary_code)
    |> then(&{ExactMatches.pick(&1), filter_predictions(&1)})

  Response.match(materials: exact_matches, predictions: predictions)  
end
```

Note: This is an important, maybe the most important, part of Match!. Even tho what it does is extremely complex, we can still understand what's going on



## for delivering changes quickly

* Thanks to the simplicity and the ecosystem provided by Elixir and Erlang, it's easy and satisfying to reliably deploy changes in production.



* Assistant has an average of [3.6 deployments per day](https://git.kci.rocks/assistant/service/-/value_stream_analytics?created_after=2022-01-01&created_before=2022-06-29&stage_id=issue&sort=end_event&direction=desc&page=1).

Note: first half of 2022, the industry standard is 1 per week, DORA considers more than once per week a metric for ELITE teams



## for interconnecting technologies

* Thanks to Elixir's active community is also possible to rely on tools and libraries developed for other popular languages.
* Given the novelty of the language, is possible that a solution to a problem simply doesn't exist yet.
* In this case is possible to combine the simplicity of Elixir with the power of other languages like Rust.

Note: Rust is a perfomance focused language with a rich ecosystem of qualitative libraries
Also because of its performance-oriented nature, is not as expressive or easy to pick up as Elixir



* In 2022 KCI published a [library](https://github.com/kloeckner-i/mail_parser) that uses Rust language for solving a problem in Assistant written in Elixir.
* The communication between Rust and Elixir is handled with the help of [Rustler](https://github.com/rusterlium/rustler)
* Our email processing algorithm relies on it.
* This allowed us to publish our code as an open source library and contributing back to the community.

Note: Adopting such innovative approach allowed us to integrate succesfully with Microsoft's GraphApi library and avoided the need of implementing the full protocol in-house



### Wrapping up



Ruby is a powerful tool that contributed to the success of many, including Kloeckner.



Elixir in KCI started as an experiment in true innovation spirit.

Note: It started as an experiment that paid generously in time, when a business assessment would have pushed for a more conservative approach.



Elixir allows us to be faster in delivering changes, helps us in preventing mistakes and to implement simple solutions to complex problems.



Even when Elixir doesn't offer an immediate solution we can combine it with other technologies for solving our needs.



_"Always code as if the guy who ends up maintaining your code will be a violent psychopath who knows where you live"_



## Questions