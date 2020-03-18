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
# <a name="protobuf-messages"></a>Zprávy ve formátu protobuf

Tato část popisuje, jak deklarovat zprávy `.proto` vyrovnávací paměti protokolu (Protobuf) v souborech. Vysvětluje základní koncepty čísla polí a typy a vypadá na kód `protoc` Jazyka C#, který generuje kompilátor.

Zbytek kapitoly se podrobněji zaměří na to, jak jsou v Protobufu zastoupeny různé typy dat.

## <a name="declaring-a-message"></a>Deklarování zprávy

V systému Windows Communication `Stock` Foundation (WCF) může být třída pro obchodní aplikaci na akciovém trhu definována jako následující příklad:

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

Chcete-li implementovat ekvivalentní třídu v Protobuf, musíte deklarovat v souboru. `.proto` Kompilátor `protoc` pak vygeneruje třídu .NET jako součást procesu sestavení.

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

První řádek deklaruje použitou syntaktickou verzi. Verze 3 jazyka byla vydána v roce 2016. Je to verze, kterou doporučujeme pro služby gRPC.

Řádek `option csharp_namespace` určuje obor názvů, který má být použit pro generované typy jazyka C#. Tato možnost bude ignorována `.proto` při kompilaci souboru pro jiné jazyky. Soubory Protobuf často obsahují možnosti specifické pro jazyk pro několik jazyků.

Definice `Stock` zprávy určuje čtyři pole. Každý z nich má typ, název a číslo pole.

## <a name="field-numbers"></a>Čísla polí

Čísla polí jsou důležitou součástí Protobufu. Používají se k identifikaci polí v binárních kódovaných datech, což znamená, že nemohou změnit z verze na verzi služby. Výhodou je, že zpětná kompatibilita a dopředná kompatibilita jsou možné. Klienti a služby budou jednoduše ignorovat čísla polí, o kterých nevědí, pokud je zpracována možnost chybějících hodnot.

V binárním formátu je číslo pole kombinováno s identifikátorem typu. Čísla polí od 1 do 15 mohou být kódována s jejich typem jako jeden bajt. Čísla od 16 do 2 047 trvá 2 bajty. Vyšší můžete, pokud potřebujete více než 2 047 polí ve zprávě z jakéhokoli důvodu. Identifikátory jednoho bajtu pro čísla polí 1 až 15 nabízejí lepší výkon, takže byste je měli použít pro nejzákladnější, často používaná pole.

## <a name="types"></a>Typy

Deklarace typu používají nativní skalární datové typy Protobuf, které jsou podrobněji popsány v [další části](protobuf-data-types.md). Zbytek této kapitoly se bude týkat předdefinovaných typů Protobuf a ukáže, jak souvisejí s běžnými typy .NET.

> [!NOTE]
> Protobuf nepodporuje nativně `decimal` typ, `double` takže se používá místo. Aplikace, které vyžadují úplnou přesnost desetinných míst, naleznete v [části o desetinných číslech](protobuf-data-types.md#decimals) v další části této kapitoly.

## <a name="the-generated-code"></a>Generovaný kód

Při vytváření aplikace Protobuf vytvoří třídy pro každou z vašich zpráv, mapování jeho nativní typy c# typy. Generovaný `Stock` typ by měl následující podpis:

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

Skutečný kód, který je generován je mnohem složitější než toto. Důvodem je, že každá třída obsahuje veškerý kód potřebný k serializaci a deserializaci do binárního formátu drátu.

### <a name="property-names"></a>Názvy vlastností

Všimněte si, že kompilátor Protobuf aplikovaný `PascalCase` na názvy vlastností, i když byly `snake_case` v souboru. `.proto` Průvodce [stylem Protobuf](https://developers.google.com/protocol-buffers/docs/style) `snake_case` doporučuje použití v definicích zpráv tak, aby generování kódu pro jiné platformy vytvořilo očekávaný případ pro jejich konvence.

>[!div class="step-by-step"]
>[Předchozí](protocol-buffers.md)
>[další](protobuf-data-types.md)
