# ToStruct

Package helps you transform maps (ex. external data) to structs (internal data).

## Example

Define a structs:

```elixir
defmodule Product do
  defstruct name: nil
end

defmodule Cart do
  defstruct id: nil,
    products: nil
end
```

Define a transformation schema and then transform a map:

```elixir
def to_struct() do
  map = %{
    "id" => 1,
    "products" => [
      %{
        "name" => "milk"
      },
      %{
        "name" => "potato",
      }
    ]
  }

  schema = %Cart{
    products: [%Product{}],
  }

  ToStruct.transform(schema, map)
end
```

## Installation

```elixir
def deps do
  [
    {:to_struct, "~> 0.1.0"}
  ]
end
```

