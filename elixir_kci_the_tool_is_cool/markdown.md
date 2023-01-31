# Kloeckner.I ❤️ Elixir



## What is Elixir?

* The programming language behind Kloeckner Assistant and other tools developed at KCI.
* It combines the syntax and the philosophy of Ruby programming language with the power of Erlang
* We use Ruby as well # TODO



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



* Ruby is considered an excellent language by many and its characteristics make it particularly suited for the development of prototypes
* Is behind many successful products like Shopify, Github and [Gitlab](https://about.gitlab.com/blog/2018/10/29/why-we-use-rails-to-build-gitlab/)



...but let's go back to Elixir...



### Elixir is...
_Elixir is a dynamic, functional language for building scalable and maintainable applications. - https://elixir-lang.org/_

Note:
Created by Jose' Valim, one of the top contributors to Ruby on Rails.
Open source and community driven.
Let's disassemble this sentence for understanding better what does it mean



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



> "Elixir is a functional language"

* Adopts a functional paradigm - "Data is immutable"
* Functional means less complexity than other commonly used paradigms


Note: Being functional is one of the characteristics that differentiates strongly Elixir from Ruby
I'll not go in the topic of comparing the different programming language paradigms in this presentation.



> "Elixir is for building scalable and maintainable applications"

Elixir is built on top of Erlang.

Erlang is a programming language built by Ericsson and released in 1986 for developing distributed systems

Note: The original purpose of Erlang was for developing systems that have to fullfill high reliability requirements, specifically telephone switches



_Erlang is used to build massively scalable soft real-time systems with requirements on high availability_ - https://www.erlang.org/



In 2023, Erlang and Elixir are battle-tested tools:
- [WhatsApp](https://www.erlang-solutions.com/blog/20-years-of-open-source-erlang-openerlang-interview-with-anton-lavrik-from-whatsapp/)
- [Cisco](https://codesync.global/media/https-youtu-be-077-xjv6plq/) for its routers
- [Discord](https://discord.com/blog/how-discord-scaled-elixir-to-5-000-000-concurrent-users)



## How Kloeckner Assistant uses Elixir?

* Assistant backend and Metadata Platform are fully implemented in Elixir
* Email processing



## Benefits

* BILLIONS OF BILLIONS OF EMAIL PER SECOND
* Gigazzilions datasets per millisecond



## Why using Elixir?

* Distributed systems
* Scalability
* Let it crash
* Allows few developers to build scalable, efficient and powerful systems




### Wrapping up