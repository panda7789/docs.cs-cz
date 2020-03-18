---
title: Protobuf výčty - gRPC pro vývojáře WCF
description: Naučte se deklarovat a používat výčty v Protobuf.
ms.date: 09/09/2019
ms.openlocfilehash: 2177f568a671fa0e651625c6e025ac70c243feb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148072"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="71d63-103">Výčty protobuf</span><span class="sxs-lookup"><span data-stu-id="71d63-103">Protobuf enumerations</span></span>

<span data-ttu-id="71d63-104">Protobuf podporuje typy výčtu.</span><span class="sxs-lookup"><span data-stu-id="71d63-104">Protobuf supports enumeration types.</span></span> <span data-ttu-id="71d63-105">Tuto podporu jste viděli v předchozí části, kde byl použit `Oneof` výčt k určení typu pole.</span><span class="sxs-lookup"><span data-stu-id="71d63-105">You saw this support in the previous section, where an enum was used to determine the type of a `Oneof` field.</span></span> <span data-ttu-id="71d63-106">Můžete definovat vlastní typy výčtu a Protobuf je zkompiluje do c# výčtu.</span><span class="sxs-lookup"><span data-stu-id="71d63-106">You can define your own enumeration types, and Protobuf will compile them to C# enum types.</span></span>

<span data-ttu-id="71d63-107">Vzhledem k tomu, že můžete použít Protobuf s různými jazyky, konvence pojmenování pro výčty se liší od c# konvence.</span><span class="sxs-lookup"><span data-stu-id="71d63-107">Because you can use Protobuf with various languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="71d63-108">Generátor kódu však převádí názvy na tradiční případ Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="71d63-108">However, the code generator converts the names to the traditional C# case.</span></span> <span data-ttu-id="71d63-109">Pokud pascal-case ekvivalent názvu pole začíná názvem výčtu, pak je odebrán.</span><span class="sxs-lookup"><span data-stu-id="71d63-109">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="71d63-110">Například v následujícím výčtu Protobuf jsou pole `ACCOUNT_STATUS`předponou .</span><span class="sxs-lookup"><span data-stu-id="71d63-110">For example, in the following Protobuf enumeration, the fields are prefixed with `ACCOUNT_STATUS`.</span></span> <span data-ttu-id="71d63-111">Tato předpona je ekvivalentní pascal-case `AccountStatus`výčtu název .</span><span class="sxs-lookup"><span data-stu-id="71d63-111">This prefix is equivalent to the Pascal-case enum name, `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="71d63-112">Generátor vytvoří výčt c# ekvivalentní následující kód:</span><span class="sxs-lookup"><span data-stu-id="71d63-112">The generator creates a C# enum equivalent to the following code:</span></span>

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

<span data-ttu-id="71d63-113">Protobuf výčtu definice *musí* mít nulovou konstantu jako jejich první pole.</span><span class="sxs-lookup"><span data-stu-id="71d63-113">Protobuf enumeration definitions *must* have a zero constant as their first field.</span></span> <span data-ttu-id="71d63-114">Stejně jako v c#, můžete deklarovat více polí se stejnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="71d63-114">As in C#, you can declare multiple fields with the same value.</span></span> <span data-ttu-id="71d63-115">Ale musíte explicitně povolit `allow_alias` tuto možnost pomocí možnosti ve výčtu:</span><span class="sxs-lookup"><span data-stu-id="71d63-115">But you must explicitly enable this option by using the `allow_alias` option in the enum:</span></span>

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

<span data-ttu-id="71d63-116">Výčty na nejvyšší úrovni v souboru `.proto` můžete deklarovat nebo vnořené v rámci definice zprávy.</span><span class="sxs-lookup"><span data-stu-id="71d63-116">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="71d63-117">Vnořené výčty – jako vnořené `.Types` zprávy – budou deklarovány v rámci statické třídy ve třídě generované zprávy.</span><span class="sxs-lookup"><span data-stu-id="71d63-117">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="71d63-118">Neexistuje žádný způsob, jak použít [[Flags]](xref:System.FlagsAttribute) atribut Protobuf generované výčtu a Protobuf nerozumí bitové výčtu kombinace.</span><span class="sxs-lookup"><span data-stu-id="71d63-118">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="71d63-119">Podívejte se na následující příklad:</span><span class="sxs-lookup"><span data-stu-id="71d63-119">Look at the following example:</span></span>

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

<span data-ttu-id="71d63-120">Pokud nastavíte `product.AvailableIn` hodnotu `Region.NorthAmerica | Region.SouthAmerica`, bude serializována `3`jako celá hodnota .</span><span class="sxs-lookup"><span data-stu-id="71d63-120">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="71d63-121">Když se klient nebo server pokusí rekonstruovat hodnotu, nenajde shodu v `3`definici výčtu pro .</span><span class="sxs-lookup"><span data-stu-id="71d63-121">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3`.</span></span> <span data-ttu-id="71d63-122">Výsledkem bude `Region.None`.</span><span class="sxs-lookup"><span data-stu-id="71d63-122">The result will be `Region.None`.</span></span>

<span data-ttu-id="71d63-123">Nejlepší způsob, jak pracovat s více hodnotami výčtu v Protobuf je použít `repeated` pole typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="71d63-123">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="71d63-124">[Předchozí](protobuf-any-oneof.md)
>[další](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="71d63-124">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
