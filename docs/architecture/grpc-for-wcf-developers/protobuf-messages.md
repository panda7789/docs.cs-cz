---
title: Zprávy Protobuf – gRPC pro vývojáře WCF
description: Přečtěte si, jak jsou Protobuf zprávy definovány v IDL a C#vygenerované v.
ms.date: 09/09/2019
ms.openlocfilehash: c7375bafb7572b0eaa0458b0310a0114e3fd078c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543037"
---
# <a name="protobuf-messages"></a><span data-ttu-id="0e53c-103">Zprávy ve formátu protobuf</span><span class="sxs-lookup"><span data-stu-id="0e53c-103">Protobuf messages</span></span>

<span data-ttu-id="0e53c-104">Tato část popisuje, jak deklarovat zprávy vyrovnávací paměti protokolu (Protobuf) v souborech `.proto`.</span><span class="sxs-lookup"><span data-stu-id="0e53c-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="0e53c-105">Vysvětluje základní koncepty čísel a typů polí a hledá C# kód, který generuje kompilátor `protoc`.</span><span class="sxs-lookup"><span data-stu-id="0e53c-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span> 

<span data-ttu-id="0e53c-106">Zbytek kapitoly se podrobněji podívá na to, jak se v Protobuf reprezentují různé typy dat.</span><span class="sxs-lookup"><span data-stu-id="0e53c-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="0e53c-107">Deklarace zprávy</span><span class="sxs-lookup"><span data-stu-id="0e53c-107">Declaring a message</span></span>

<span data-ttu-id="0e53c-108">V Windows Communication Foundation (WCF) může být `Stock`á třída pro obchodní obchodní aplikace, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0e53c-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

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

<span data-ttu-id="0e53c-109">Chcete-li implementovat ekvivalentní třídu v Protobuf, je nutné ji deklarovat v souboru `.proto`.</span><span class="sxs-lookup"><span data-stu-id="0e53c-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="0e53c-110">Kompilátor `protoc` pak vygeneruje třídu .NET jako součást procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="0e53c-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

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

<span data-ttu-id="0e53c-111">První řádek deklaruje použitou verzi syntaxe.</span><span class="sxs-lookup"><span data-stu-id="0e53c-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="0e53c-112">Verze 3 jazyka byla vydaná v 2016.</span><span class="sxs-lookup"><span data-stu-id="0e53c-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="0e53c-113">Je to verze, kterou doporučujeme pro služby gRPC Services.</span><span class="sxs-lookup"><span data-stu-id="0e53c-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="0e53c-114">`option csharp_namespace` řádek určuje obor názvů, který se má použít pro generované C# typy.</span><span class="sxs-lookup"><span data-stu-id="0e53c-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="0e53c-115">Tato možnost bude ignorována, pokud je soubor `.proto` kompilován pro jiné jazyky.</span><span class="sxs-lookup"><span data-stu-id="0e53c-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="0e53c-116">Soubory Protobuf často obsahují možnosti specifické pro konkrétní jazyk v několika jazycích.</span><span class="sxs-lookup"><span data-stu-id="0e53c-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="0e53c-117">Definice `Stock` zprávy určuje čtyři pole.</span><span class="sxs-lookup"><span data-stu-id="0e53c-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="0e53c-118">Každá z nich má typ, název a číslo pole.</span><span class="sxs-lookup"><span data-stu-id="0e53c-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="0e53c-119">Čísla polí</span><span class="sxs-lookup"><span data-stu-id="0e53c-119">Field numbers</span></span>

<span data-ttu-id="0e53c-120">Čísla polí jsou důležitou součástí Protobufu.</span><span class="sxs-lookup"><span data-stu-id="0e53c-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="0e53c-121">Používají se k identifikaci polí v binárních kódovaných datech, což znamená, že se nemůžou změnit z verze na verzi vaší služby.</span><span class="sxs-lookup"><span data-stu-id="0e53c-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="0e53c-122">Výhodou je, že je možné zpětná kompatibilita a dopředná kompatibilita.</span><span class="sxs-lookup"><span data-stu-id="0e53c-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="0e53c-123">Klienti a služby budou jednoduše ignorovat čísla polí, o kterých neznají, pokud je zpracována možnost chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0e53c-123">Clients and services will simply ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="0e53c-124">V binárním formátu je číslo pole kombinováno s identifikátorem typu.</span><span class="sxs-lookup"><span data-stu-id="0e53c-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="0e53c-125">Čísla polí od 1 do 15 lze kódovat s jejich typem jako jeden bajt.</span><span class="sxs-lookup"><span data-stu-id="0e53c-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="0e53c-126">Čísla od 16 do 2 047 pobírají 2 bajty.</span><span class="sxs-lookup"><span data-stu-id="0e53c-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="0e53c-127">Pokud z jakéhokoli důvodu potřebujete více než 2 047 polí, můžete přejít na vyšší.</span><span class="sxs-lookup"><span data-stu-id="0e53c-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="0e53c-128">Identifikátory jednoho bajtu pro čísla polí 1 až 15 nabízejí lepší výkon, takže je byste měli použít pro většinu základních, často používaných polí.</span><span class="sxs-lookup"><span data-stu-id="0e53c-128">The single byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="0e53c-129">Typy</span><span class="sxs-lookup"><span data-stu-id="0e53c-129">Types</span></span>

<span data-ttu-id="0e53c-130">Deklarace typu používají nativní skalární datové typy Protobuf, které jsou podrobněji popsány v [následující části](protobuf-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="0e53c-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="0e53c-131">Zbytek této kapitoly se zabývá vestavěnými typy Protobuf a ukazuje, jak se vztahují na běžné typy .NET.</span><span class="sxs-lookup"><span data-stu-id="0e53c-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="0e53c-132">Protobuf netivně podporuje `decimal` typ, takže se místo toho použije `double`.</span><span class="sxs-lookup"><span data-stu-id="0e53c-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="0e53c-133">Pro aplikace, které vyžadují plnou desítkovou přesnost, se podívejte na [část na desetinných číslech](protobuf-data-types.md#decimals) v další části této kapitoly.</span><span class="sxs-lookup"><span data-stu-id="0e53c-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="0e53c-134">Generovaný kód</span><span class="sxs-lookup"><span data-stu-id="0e53c-134">The generated code</span></span>

<span data-ttu-id="0e53c-135">Při sestavování aplikace Protobuf vytvoří třídy pro každou vaši zprávu a namapuje jejich nativní typy na C# typy.</span><span class="sxs-lookup"><span data-stu-id="0e53c-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="0e53c-136">Vygenerovaný `Stock` typ by měl následující signaturu:</span><span class="sxs-lookup"><span data-stu-id="0e53c-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="0e53c-137">Skutečný kód, který je generován, je mnohem složitější než tento.</span><span class="sxs-lookup"><span data-stu-id="0e53c-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="0e53c-138">Důvodem je, že každá třída obsahuje veškerý kód potřebný k serializaci a deserializaci sebe sama do binárního formátu.</span><span class="sxs-lookup"><span data-stu-id="0e53c-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="0e53c-139">Názvy vlastností</span><span class="sxs-lookup"><span data-stu-id="0e53c-139">Property names</span></span>

<span data-ttu-id="0e53c-140">Všimněte si, že kompilátor Protobuf použili `PascalCase` k názvům vlastností, i když byly `snake_case` v souboru `.proto`.</span><span class="sxs-lookup"><span data-stu-id="0e53c-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="0e53c-141">[Průvodce stylem Protobuf](https://developers.google.com/protocol-buffers/docs/style) doporučuje použít `snake_case` ve vašich definicích zpráv, aby generování kódu pro jiné platformy vytvořilo očekávaný případ pro jejich konvence.</span><span class="sxs-lookup"><span data-stu-id="0e53c-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0e53c-142">[Předchozí](protocol-buffers.md)
>[Další](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="0e53c-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
