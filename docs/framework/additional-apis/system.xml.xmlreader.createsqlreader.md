---
title: Metoda XmlReader.CreateSqlReader (System.Xml)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 7bd2ef5158516acede47f73f9937d06159bc16c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155736"
---
# <a name="xmlreadercreatesqlreader-method"></a>XmlReader.CreateSqlReader – metoda

Vytvoří novou <xref:System.Xml.XmlReader> instanci pomocí zadaného datového proudu, nastavení a kontextových informací pro analýzu.

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>Parametry

- `input` <xref:System.IO.Stream>  
  Datový proud, který obsahuje data XML.

- `settings` <xref:System.Xml.XmlReaderSettings>  
  Nastavení pro novou <xref:System.Xml.XmlReader> instanci. Tato hodnota `null`může být .

- `inputContext` <xref:System.Xml.XmlParserContext>  
  Kontextové informace potřebné k analýzě fragmentu XML. Tato hodnota `null`může být .

## <a name="returns"></a>Vrací

<xref:System.Xml.XmlReader>  
Objekt, který se používá ke čtení dat XML v datovém proudu.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Metoda `XmlReader.CreateSqlReader` je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft nepodporuje použití této metody v produkční aplikaci za žádných okolností.

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Xml>

**Sestava:** Soubor System.Xml.dll

**Verze rozhraní .NET Framework:** K dispozici od 2.0.
