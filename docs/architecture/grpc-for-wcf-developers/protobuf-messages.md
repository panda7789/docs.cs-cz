---
title: Zprávy Protobuf – gRPC pro vývojáře WCF
description: Přečtěte si, jak jsou Protobuf zprávy definovány v IDL a C#vygenerované v.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 1fdbedaadb33ac3eb99ca360018beb36ac7a8d78
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771624"
---
# <a name="protobuf-messages"></a>Zprávy ve formátu protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

V této části se dozvíte, jak deklarovat zprávy Protobuf v souborech `.proto`, vysvětluje základní koncepty čísel a typů polí a vyhledává se C# v kódu, který je generován kompilátorem `protoc`. Zbytek kapitoly se podrobněji podívá na to, jak se v Protobuf reprezentují různé typy dat.

## <a name="declaring-a-message"></a>Deklarace zprávy

Ve službě WCF může být `Stock` třída pro obchodní obchodní aplikace, jak je uvedeno v následujícím příkladu:

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

Chcete-li implementovat ekvivalentní třídu v Protobuf, musí být deklarována v souboru `.proto`. Kompilátor `protoc` pak vygeneruje třídu .NET jako součást procesu sestavení.

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

První řádek deklaruje použitou verzi syntaxe. Verze 3 jazyka byla vydána v 2016 a jedná se o doporučenou verzi pro služby gRPC Services.

@No__t_0 řádek určuje obor názvů, který se má použít pro generované C# typy. Tato možnost bude ignorována, pokud je soubor `.proto` kompilován pro jiné jazyky. Pro soubory Protobuf je běžné, že obsahují možnosti specifické pro jazyk pro několik jazyků.

Definice `Stock` zprávy určuje čtyři pole, každý s typem, název a číslo pole.

## <a name="field-numbers"></a>Čísla polí

Čísla polí jsou důležitou součástí Protobufu. Používají se k identifikaci polí v binárních kódovaných datech, což znamená, že se nemůžou změnit z verze na verzi vaší služby. Výhodou je to, že zpětná a dopředná kompatibilita je možná. Klienti a služby budou jednoduše ignorovat čísla polí, která neznají, pokud je zpracována možnost chybějící hodnoty.

V binárním formátu je číslo pole kombinováno s identifikátorem typu. Čísla polí od 1 do 15 je možné kódovat s jejich typem jako jeden bajt. čísla od 16 do 2047 pobírají 2 bajty. Pokud z jakéhokoli důvodu potřebujete více než 2047 polí, můžete přejít na vyšší. Identifikátory jednoho bajtu pro čísla polí 1 až 15 nabízejí lepší výkon, takže je byste měli použít pro většinu základních, často používaných polí.

## <a name="types"></a>Typy

Deklarace typu používají nativní skalární datové typy Protobuf, které jsou podrobněji popsány v [následující části](protobuf-data-types.md). Zbytek této kapitoly se zabývá vestavěnými typy Protobuf a ukazuje, jak se vztahují na běžné typy .NET.

> [!NOTE]
> Protobuf netivně podporuje `decimal` typ, takže se místo toho použije Double. Pro aplikace, které vyžadují plnou desítkovou přesnost, se podívejte na [část na desetinných číslech](protobuf-data-types.md#decimals) v další části této kapitoly.

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

Skutečný kód, který je generován, je mnohem složitější než to, protože každá třída obsahuje veškerý kód potřebný k serializaci a deserializaci do binárního formátu.

### <a name="property-names"></a>Názvy vlastností

Všimněte si, že kompilátor Protobuf použili `PascalCase` k názvům vlastností, i když byly `snake_case` v souboru `.proto`. [Průvodce stylem Protobuf](https://developers.google.com/protocol-buffers/docs/style) doporučuje použít `snake_case` ve vašich definicích zpráv, aby generování kódu pro jiné platformy vytvořilo očekávaný případ pro jejich konvence.

>[!div class="step-by-step"]
>[Předchozí](protocol-buffers.md)
>[Další](protobuf-data-types.md)
