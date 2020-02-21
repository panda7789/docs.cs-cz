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
# <a name="protobuf-messages"></a>Zprávy ve formátu protobuf

Tato část popisuje, jak deklarovat zprávy vyrovnávací paměti protokolu (Protobuf) v souborech `.proto`. Vysvětluje základní koncepty čísel a typů polí a hledá C# kód, který generuje kompilátor `protoc`. 

Zbytek kapitoly se podrobněji podívá na to, jak se v Protobuf reprezentují různé typy dat.

## <a name="declaring-a-message"></a>Deklarace zprávy

V Windows Communication Foundation (WCF) může být `Stock`á třída pro obchodní obchodní aplikace, jak je uvedeno v následujícím příkladu:

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

Chcete-li implementovat ekvivalentní třídu v Protobuf, je nutné ji deklarovat v souboru `.proto`. Kompilátor `protoc` pak vygeneruje třídu .NET jako součást procesu sestavení.

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

První řádek deklaruje použitou verzi syntaxe. Verze 3 jazyka byla vydaná v 2016. Je to verze, kterou doporučujeme pro služby gRPC Services.

`option csharp_namespace` řádek určuje obor názvů, který se má použít pro generované C# typy. Tato možnost bude ignorována, pokud je soubor `.proto` kompilován pro jiné jazyky. Soubory Protobuf často obsahují možnosti specifické pro konkrétní jazyk v několika jazycích.

Definice `Stock` zprávy určuje čtyři pole. Každá z nich má typ, název a číslo pole.

## <a name="field-numbers"></a>Čísla polí

Čísla polí jsou důležitou součástí Protobufu. Používají se k identifikaci polí v binárních kódovaných datech, což znamená, že se nemůžou změnit z verze na verzi vaší služby. Výhodou je, že je možné zpětná kompatibilita a dopředná kompatibilita. Klienti a služby budou jednoduše ignorovat čísla polí, o kterých neznají, pokud je zpracována možnost chybějící hodnoty.

V binárním formátu je číslo pole kombinováno s identifikátorem typu. Čísla polí od 1 do 15 lze kódovat s jejich typem jako jeden bajt. Čísla od 16 do 2 047 pobírají 2 bajty. Pokud z jakéhokoli důvodu potřebujete více než 2 047 polí, můžete přejít na vyšší. Identifikátory jednoho bajtu pro čísla polí 1 až 15 nabízejí lepší výkon, takže je byste měli použít pro většinu základních, často používaných polí.

## <a name="types"></a>Typy

Deklarace typu používají nativní skalární datové typy Protobuf, které jsou podrobněji popsány v [následující části](protobuf-data-types.md). Zbytek této kapitoly se zabývá vestavěnými typy Protobuf a ukazuje, jak se vztahují na běžné typy .NET.

> [!NOTE]
> Protobuf netivně podporuje `decimal` typ, takže se místo toho použije `double`. Pro aplikace, které vyžadují plnou desítkovou přesnost, se podívejte na [část na desetinných číslech](protobuf-data-types.md#decimals) v další části této kapitoly.

## <a name="the-generated-code"></a>Generovaný kód

Při sestavování aplikace Protobuf vytvoří třídy pro každou vaši zprávu a namapuje jejich nativní typy na C# typy. Vygenerovaný `Stock` typ by měl následující signaturu:

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

Všimněte si, že kompilátor Protobuf použili `PascalCase` k názvům vlastností, i když byly `snake_case` v souboru `.proto`. [Průvodce stylem Protobuf](https://developers.google.com/protocol-buffers/docs/style) doporučuje použít `snake_case` ve vašich definicích zpráv, aby generování kódu pro jiné platformy vytvořilo očekávaný případ pro jejich konvence.

>[!div class="step-by-step"]
>[Předchozí](protocol-buffers.md)
>[Další](protobuf-data-types.md)
