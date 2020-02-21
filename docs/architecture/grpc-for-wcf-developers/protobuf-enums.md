---
title: Výčty Protobuf – gRPC pro vývojáře WCF
description: Naučte se deklarovat a používat výčty v Protobuf.
ms.date: 09/09/2019
ms.openlocfilehash: 01cf4a4e5e0eda1e7ddff2a6780119fcb3120dad
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543141"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="902ea-103">Výčty protobuf</span><span class="sxs-lookup"><span data-stu-id="902ea-103">Protobuf enumerations</span></span>

<span data-ttu-id="902ea-104">Protobuf podporuje výčtové typy.</span><span class="sxs-lookup"><span data-stu-id="902ea-104">Protobuf supports enumeration types.</span></span> <span data-ttu-id="902ea-105">Tuto podporu jste viděli v předchozí části, kde byl k určení typu `Oneof` pole použit výčet.</span><span class="sxs-lookup"><span data-stu-id="902ea-105">You saw this support in the previous section, where an enum was used to determine the type of a `Oneof` field.</span></span> <span data-ttu-id="902ea-106">Můžete definovat vlastní typy výčtu a Protobuf je zkompiluje do C# výčtových typů.</span><span class="sxs-lookup"><span data-stu-id="902ea-106">You can define your own enumeration types, and Protobuf will compile them to C# enum types.</span></span> 

<span data-ttu-id="902ea-107">Vzhledem k tomu, že můžete používat Protobuf s různými jazyky, zásady vytváření názvů pro výčty se C# liší od konvencí.</span><span class="sxs-lookup"><span data-stu-id="902ea-107">Because you can use Protobuf with various languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="902ea-108">Generátor kódu však převede názvy na tradiční C# případ.</span><span class="sxs-lookup"><span data-stu-id="902ea-108">However, the code generator converts the names to the traditional C# case.</span></span> <span data-ttu-id="902ea-109">Pokud je ekvivalent názvu pole v jazyce Pascal shodný s názvem výčtu, bude odstraněn.</span><span class="sxs-lookup"><span data-stu-id="902ea-109">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="902ea-110">Například v následujícím výčtu Protobuf jsou pole s předponou `ACCOUNT_STATUS`.</span><span class="sxs-lookup"><span data-stu-id="902ea-110">For example, in the following Protobuf enumeration, the fields are prefixed with `ACCOUNT_STATUS`.</span></span> <span data-ttu-id="902ea-111">Tato předpona je shodná s názvem Pascal-Case Enum, `AccountStatus`.</span><span class="sxs-lookup"><span data-stu-id="902ea-111">This prefix is equivalent to the Pascal-case enum name, `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="902ea-112">Generátor vytvoří C# výčet podobný následujícímu kódu:</span><span class="sxs-lookup"><span data-stu-id="902ea-112">The generator creates a C# enum equivalent to the following code:</span></span>

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

<span data-ttu-id="902ea-113">Definice výčtu Protobuf *musí* mít jako první pole nulovou konstantu.</span><span class="sxs-lookup"><span data-stu-id="902ea-113">Protobuf enumeration definitions *must* have a zero constant as their first field.</span></span> <span data-ttu-id="902ea-114">Jako v C#můžete deklarovat více polí se stejnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="902ea-114">As in C#, you can declare multiple fields with the same value.</span></span> <span data-ttu-id="902ea-115">Tuto možnost však musíte explicitně povolit pomocí možnosti `allow_alias` ve výčtu:</span><span class="sxs-lookup"><span data-stu-id="902ea-115">But you must explicitly enable this option by using the `allow_alias` option in the enum:</span></span>

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

<span data-ttu-id="902ea-116">Výčty můžete deklarovat na nejvyšší úrovni v souboru `.proto` nebo jsou vnořené v rámci definice zprávy.</span><span class="sxs-lookup"><span data-stu-id="902ea-116">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="902ea-117">Vnořené výčty – podobně jako vnořené zprávy – budou deklarovány v rámci `.Types` statické třídy ve třídě generované zprávy.</span><span class="sxs-lookup"><span data-stu-id="902ea-117">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="902ea-118">Neexistuje žádný způsob, jak použít atribut [[Flags]](xref:System.FlagsAttribute) u výčtu generovaného Protobuf a Protobuf nerozumí kombinací bitových výčtů.</span><span class="sxs-lookup"><span data-stu-id="902ea-118">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="902ea-119">Podívejte se na následující příklad:</span><span class="sxs-lookup"><span data-stu-id="902ea-119">Look at the following example:</span></span>

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region available_in = 1;
}
```

<span data-ttu-id="902ea-120">Nastavíte-li `product.AvailableIn` na `Region.NorthAmerica | Region.SouthAmerica`, je serializován jako celočíselná hodnota `3`.</span><span class="sxs-lookup"><span data-stu-id="902ea-120">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="902ea-121">Když se klient nebo server pokusí hodnotu deserializovat, nenajde shodu v definici výčtu pro `3`.</span><span class="sxs-lookup"><span data-stu-id="902ea-121">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3`.</span></span> <span data-ttu-id="902ea-122">Výsledek bude `Region.None`.</span><span class="sxs-lookup"><span data-stu-id="902ea-122">The result will be `Region.None`.</span></span>

<span data-ttu-id="902ea-123">Nejlepším způsobem, jak pracovat s více hodnotami výčtu v Protobuf, je použít pole `repeated` typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="902ea-123">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="902ea-124">[Předchozí](protobuf-any-oneof.md)
>[Další](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="902ea-124">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
