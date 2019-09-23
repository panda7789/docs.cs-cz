---
title: Výčty Protobuf – gRPC pro vývojáře WCF
description: Naučte se deklarovat a používat výčty v Protobuf.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d93319b713588129a19246976a82bb03a90ce680
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184237"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="57e7a-103">Výčty Protobuf</span><span class="sxs-lookup"><span data-stu-id="57e7a-103">Protobuf enumerations</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="57e7a-104">Protobuf podporuje výčtové typy, jak je vidět v předchozí části, kde byl pro určení typu `oneof` pole použit výčet.</span><span class="sxs-lookup"><span data-stu-id="57e7a-104">Protobuf supports enumeration types, as seen in the previous section where an enum was used to determine the type of a `oneof` field.</span></span> <span data-ttu-id="57e7a-105">Můžete definovat vlastní typy výčtu a Protobuf je zkompiluje do C# výčtových typů.</span><span class="sxs-lookup"><span data-stu-id="57e7a-105">You can define your own enumeration types and Protobuf will compile them to C# enum types.</span></span> <span data-ttu-id="57e7a-106">Vzhledem k tomu, že Protobuf lze použít s různými jazyky, zásady vytváření názvů pro výčty se C# liší od konvencí.</span><span class="sxs-lookup"><span data-stu-id="57e7a-106">Since Protobuf can be used with different languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="57e7a-107">Generátor kódu je však chytřejší a převádí názvy na tradiční C# případ.</span><span class="sxs-lookup"><span data-stu-id="57e7a-107">However, the code generator is clever and converts the names to the traditional C# case.</span></span> <span data-ttu-id="57e7a-108">Pokud je ekvivalent názvu pole v jazyce Pascal shodný s názvem výčtu, bude odstraněn.</span><span class="sxs-lookup"><span data-stu-id="57e7a-108">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="57e7a-109">Například v tomto výčtu Protobuf jsou pole předponou `ACCOUNT_STATUS`, což je ekvivalent názvu výčtu Case Case:. `AccountStatus`</span><span class="sxs-lookup"><span data-stu-id="57e7a-109">For example, in this Protobuf enumeration the fields are prefixed with `ACCOUNT_STATUS`, which is equivalent to the Pascal case enum name: `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="57e7a-110">Generátor proto vytvoří C# výčet podobný následujícímu kódu:</span><span class="sxs-lookup"><span data-stu-id="57e7a-110">So, the generator creates a C# enum equivalent to the following code:</span></span>

```csharp
public enum AccountStatus
{
    Unknown = 0,
    Pending = 1,
    Active = 2,
    Suspended = 3,
    Closed = 4
}
```

<span data-ttu-id="57e7a-111">Definice výčtu Protobuf **musí** mít jako první pole nulovou konstantu.</span><span class="sxs-lookup"><span data-stu-id="57e7a-111">Protobuf enumeration definitions **must** have a zero constant as their first field.</span></span> <span data-ttu-id="57e7a-112">Jako v C#můžete deklarovat více polí se stejnou hodnotou, ale tuto možnost musíte explicitně povolit pomocí `allow_alias` možnosti ve výčtu:</span><span class="sxs-lookup"><span data-stu-id="57e7a-112">As in C#, you can declare multiple fields with the same value, but you must explicitly enable this option using the `allow_alias` option in the enum:</span></span>

```protobuf
enum AccountStatus {
  option allow_alias = true;
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
  ACCOUNT_STATUS_CANCELLED = 4;
}
```

<span data-ttu-id="57e7a-113">Výčty můžete deklarovat na nejvyšší úrovni v `.proto` souboru nebo v definici zprávy.</span><span class="sxs-lookup"><span data-stu-id="57e7a-113">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="57e7a-114">Vnořené výčty – podobně jako vnořené zprávy – budou deklarovány v `.Types` rámci statické třídy ve třídě vygenerované zprávy.</span><span class="sxs-lookup"><span data-stu-id="57e7a-114">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="57e7a-115">Neexistuje žádný způsob, jak použít atribut [[Flags]](xref:System.FlagsAttribute) u výčtu generovaného Protobuf a Protobuf nerozumí kombinací bitových výčtů.</span><span class="sxs-lookup"><span data-stu-id="57e7a-115">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="57e7a-116">Podívejte se na následující příklad:</span><span class="sxs-lookup"><span data-stu-id="57e7a-116">Take a look at the following example:</span></span>

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region availableIn = 1;
}
```

<span data-ttu-id="57e7a-117">Pokud nastavíte `product.AvailableIn` na `Region.NorthAmerica | Region.SouthAmerica`, je serializován jako celočíselná hodnota `3`.</span><span class="sxs-lookup"><span data-stu-id="57e7a-117">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="57e7a-118">Když se klient nebo server pokusí hodnotu deserializovat, nenajde shodu v definici výčtu pro `3` a výsledek `Region.None`bude.</span><span class="sxs-lookup"><span data-stu-id="57e7a-118">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3` and the result will be `Region.None`.</span></span>

<span data-ttu-id="57e7a-119">Nejlepším způsobem, jak pracovat s více hodnotami výčtu v Protobuf, je použít `repeated` pole typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="57e7a-119">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="57e7a-120">[Předchozí](protobuf-any-oneof.md)
>[Další](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="57e7a-120">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
