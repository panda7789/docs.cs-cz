---
title: Protobuf zprávy - gRPC pro vývojáře WCF
description: Zjistěte, jak jsou zprávy Protobuf definovány v IDL a generovány v c#.
ms.date: 09/09/2019
ms.openlocfilehash: 5b3d4383de39a3785ef804fec21939a740f54669
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147981"
---
# <a name="protobuf-messages"></a><span data-ttu-id="041a7-103">Zprávy ve formátu protobuf</span><span class="sxs-lookup"><span data-stu-id="041a7-103">Protobuf messages</span></span>

<span data-ttu-id="041a7-104">Tato část popisuje, jak deklarovat zprávy `.proto` vyrovnávací paměti protokolu (Protobuf) v souborech.</span><span class="sxs-lookup"><span data-stu-id="041a7-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="041a7-105">Vysvětluje základní koncepty čísla polí a typy a vypadá na kód `protoc` Jazyka C#, který generuje kompilátor.</span><span class="sxs-lookup"><span data-stu-id="041a7-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span>

<span data-ttu-id="041a7-106">Zbytek kapitoly se podrobněji zaměří na to, jak jsou v Protobufu zastoupeny různé typy dat.</span><span class="sxs-lookup"><span data-stu-id="041a7-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="041a7-107">Deklarování zprávy</span><span class="sxs-lookup"><span data-stu-id="041a7-107">Declaring a message</span></span>

<span data-ttu-id="041a7-108">V systému Windows Communication `Stock` Foundation (WCF) může být třída pro obchodní aplikaci na akciovém trhu definována jako následující příklad:</span><span class="sxs-lookup"><span data-stu-id="041a7-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

<span data-ttu-id="041a7-109">Chcete-li implementovat ekvivalentní třídu v Protobuf, musíte deklarovat v souboru. `.proto`</span><span class="sxs-lookup"><span data-stu-id="041a7-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="041a7-110">Kompilátor `protoc` pak vygeneruje třídu .NET jako součást procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="041a7-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

<span data-ttu-id="041a7-111">První řádek deklaruje použitou syntaktickou verzi.</span><span class="sxs-lookup"><span data-stu-id="041a7-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="041a7-112">Verze 3 jazyka byla vydána v roce 2016.</span><span class="sxs-lookup"><span data-stu-id="041a7-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="041a7-113">Je to verze, kterou doporučujeme pro služby gRPC.</span><span class="sxs-lookup"><span data-stu-id="041a7-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="041a7-114">Řádek `option csharp_namespace` určuje obor názvů, který má být použit pro generované typy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="041a7-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="041a7-115">Tato možnost bude ignorována `.proto` při kompilaci souboru pro jiné jazyky.</span><span class="sxs-lookup"><span data-stu-id="041a7-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="041a7-116">Soubory Protobuf často obsahují možnosti specifické pro jazyk pro několik jazyků.</span><span class="sxs-lookup"><span data-stu-id="041a7-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="041a7-117">Definice `Stock` zprávy určuje čtyři pole.</span><span class="sxs-lookup"><span data-stu-id="041a7-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="041a7-118">Každý z nich má typ, název a číslo pole.</span><span class="sxs-lookup"><span data-stu-id="041a7-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="041a7-119">Čísla polí</span><span class="sxs-lookup"><span data-stu-id="041a7-119">Field numbers</span></span>

<span data-ttu-id="041a7-120">Čísla polí jsou důležitou součástí Protobufu.</span><span class="sxs-lookup"><span data-stu-id="041a7-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="041a7-121">Používají se k identifikaci polí v binárních kódovaných datech, což znamená, že nemohou změnit z verze na verzi služby.</span><span class="sxs-lookup"><span data-stu-id="041a7-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="041a7-122">Výhodou je, že zpětná kompatibilita a dopředná kompatibilita jsou možné.</span><span class="sxs-lookup"><span data-stu-id="041a7-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="041a7-123">Klienti a služby budou jednoduše ignorovat čísla polí, o kterých nevědí, pokud je zpracována možnost chybějících hodnot.</span><span class="sxs-lookup"><span data-stu-id="041a7-123">Clients and services will simply ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="041a7-124">V binárním formátu je číslo pole kombinováno s identifikátorem typu.</span><span class="sxs-lookup"><span data-stu-id="041a7-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="041a7-125">Čísla polí od 1 do 15 mohou být kódována s jejich typem jako jeden bajt.</span><span class="sxs-lookup"><span data-stu-id="041a7-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="041a7-126">Čísla od 16 do 2 047 trvá 2 bajty.</span><span class="sxs-lookup"><span data-stu-id="041a7-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="041a7-127">Vyšší můžete, pokud potřebujete více než 2 047 polí ve zprávě z jakéhokoli důvodu.</span><span class="sxs-lookup"><span data-stu-id="041a7-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="041a7-128">Identifikátory jednoho bajtu pro čísla polí 1 až 15 nabízejí lepší výkon, takže byste je měli použít pro nejzákladnější, často používaná pole.</span><span class="sxs-lookup"><span data-stu-id="041a7-128">The single byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="041a7-129">Typy</span><span class="sxs-lookup"><span data-stu-id="041a7-129">Types</span></span>

<span data-ttu-id="041a7-130">Deklarace typu používají nativní skalární datové typy Protobuf, které jsou podrobněji popsány v [další části](protobuf-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="041a7-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="041a7-131">Zbytek této kapitoly se bude týkat předdefinovaných typů Protobuf a ukáže, jak souvisejí s běžnými typy .NET.</span><span class="sxs-lookup"><span data-stu-id="041a7-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="041a7-132">Protobuf nepodporuje nativně `decimal` typ, `double` takže se používá místo.</span><span class="sxs-lookup"><span data-stu-id="041a7-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="041a7-133">Aplikace, které vyžadují úplnou přesnost desetinných míst, naleznete v [části o desetinných číslech](protobuf-data-types.md#decimals) v další části této kapitoly.</span><span class="sxs-lookup"><span data-stu-id="041a7-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="041a7-134">Generovaný kód</span><span class="sxs-lookup"><span data-stu-id="041a7-134">The generated code</span></span>

<span data-ttu-id="041a7-135">Při vytváření aplikace Protobuf vytvoří třídy pro každou z vašich zpráv, mapování jeho nativní typy c# typy.</span><span class="sxs-lookup"><span data-stu-id="041a7-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="041a7-136">Generovaný `Stock` typ by měl následující podpis:</span><span class="sxs-lookup"><span data-stu-id="041a7-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="041a7-137">Skutečný kód, který je generován je mnohem složitější než toto.</span><span class="sxs-lookup"><span data-stu-id="041a7-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="041a7-138">Důvodem je, že každá třída obsahuje veškerý kód potřebný k serializaci a deserializaci do binárního formátu drátu.</span><span class="sxs-lookup"><span data-stu-id="041a7-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="041a7-139">Názvy vlastností</span><span class="sxs-lookup"><span data-stu-id="041a7-139">Property names</span></span>

<span data-ttu-id="041a7-140">Všimněte si, že kompilátor Protobuf aplikovaný `PascalCase` na názvy vlastností, i když byly `snake_case` v souboru. `.proto`</span><span class="sxs-lookup"><span data-stu-id="041a7-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="041a7-141">Průvodce [stylem Protobuf](https://developers.google.com/protocol-buffers/docs/style) `snake_case` doporučuje použití v definicích zpráv tak, aby generování kódu pro jiné platformy vytvořilo očekávaný případ pro jejich konvence.</span><span class="sxs-lookup"><span data-stu-id="041a7-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="041a7-142">[Předchozí](protocol-buffers.md)
>[další](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="041a7-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
