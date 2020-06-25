---
title: Zprávy Protobuf – gRPC pro vývojáře WCF
description: Přečtěte si, jak jsou Protobuf zprávy definovány v IDL a vygenerované v jazyce C#.
ms.date: 09/09/2019
ms.openlocfilehash: 6fc7b9c34810abaa8d674af56d1517a5cf87521b
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325040"
---
# <a name="protobuf-messages"></a>Zprávy ve formátu protobuf

Tato část popisuje, jak deklarovat zprávy vyrovnávací paměti protokolu (Protobuf) v `.proto` souborech. Vysvětluje základní koncepty čísel a typů polí a hledá kód C#, který `protoc` kompilátor generuje.

Zbytek kapitoly se podrobněji podívá na to, jak se v Protobuf reprezentují různé typy dat.

## <a name="declaring-a-message"></a>Deklarace zprávy

V Windows Communication Foundation (WCF) je `Stock` možné definovat třídu pro obchodní aplikace na burze trhu jako v následujícím příkladu:

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

Chcete-li implementovat ekvivalentní třídu v Protobuf, je nutné ji deklarovat v `.proto` souboru. `protoc`Kompilátor poté vytvoří třídu .NET jako součást procesu sestavení.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

První řádek deklaruje použitou verzi syntaxe. Verze 3 jazyka byla vydaná v 2016. Je to verze, kterou doporučujeme pro služby gRPC Services.

`option csharp_namespace`Řádek určuje obor názvů, který se má použít pro vygenerované typy C#. Tato možnost bude ignorována, pokud `.proto` je soubor zkompilován pro jiné jazyky. Soubory Protobuf často obsahují možnosti specifické pro konkrétní jazyk v několika jazycích.

`Stock`Definice zprávy určuje čtyři pole. Každá z nich má typ, název a číslo pole.

## <a name="field-numbers"></a>Čísla polí

Čísla polí jsou důležitou součástí Protobufu. Používají se k identifikaci polí v binárních kódovaných datech, což znamená, že se nemůžou změnit z verze na verzi vaší služby. Výhodou je, že je možné zpětná kompatibilita a dopředná kompatibilita. Klienti a služby budou jednoduše ignorovat čísla polí, o kterých neznají, pokud je zpracována možnost chybějící hodnoty.

V binárním formátu je číslo pole kombinováno s identifikátorem typu. Čísla polí od 1 do 15 lze kódovat s jejich typem jako jeden bajt. Čísla od 16 do 2 047 pobírají 2 bajty. Pokud z jakéhokoli důvodu potřebujete více než 2 047 polí, můžete přejít na vyšší. Identifikátory jednoho bajtu pro čísla polí 1 až 15 nabízejí lepší výkon, takže je byste měli použít pro většinu základních, často používaných polí.

## <a name="types"></a>Typy

Deklarace typu používají nativní skalární datové typy Protobuf, které jsou podrobněji popsány v [následující části](protobuf-data-types.md). Zbytek této kapitoly se zabývá vestavěnými typy Protobuf a ukazuje, jak se vztahují na běžné typy .NET.

> [!NOTE]
> Protobuf nedokáže nativně podporovat `decimal` typ, takže `double` se místo toho použije. Pro aplikace, které vyžadují plnou desítkovou přesnost, se podívejte na [část na desetinných číslech](protobuf-data-types.md#decimals) v další části této kapitoly.

## <a name="the-generated-code"></a>Generovaný kód

Při sestavování aplikace Protobuf vytvoří třídy pro každou vaši zprávu a namapuje jejich nativní typy na typy jazyka C#. Vygenerovaný `Stock` typ by měl následující signaturu:

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

Skutečný kód, který je generován, je mnohem složitější než tento. Důvodem je, že každá třída obsahuje veškerý kód potřebný k serializaci a deserializaci sebe sama do binárního formátu.

### <a name="property-names"></a>Názvy vlastností

Všimněte si, že kompilátor Protobuf se aplikuje `PascalCase` na názvy vlastností, i když byly `snake_case` v `.proto` souboru. [Průvodce stylem Protobuf](https://developers.google.com/protocol-buffers/docs/style) doporučuje použití `snake_case` ve vašich definicích zpráv, aby generování kódu pro jiné platformy vytvořilo očekávaný případ pro své konvence.

>[!div class="step-by-step"]
>[Předchozí](protocol-buffers.md) 
> [Další](protobuf-data-types.md)
