---
title: XmlReader. CreateSqlReader – metoda (System. XML)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: c65ef7c073175488c11c5e912a44d46fd4319209
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215452"
---
# <a name="xmlreadercreatesqlreader-method"></a>XmlReader.CreateSqlReader – metoda

Vytvoří novou instanci <xref:System.Xml.XmlReader> pomocí zadaného datového proudu, nastavení a kontextové informace pro analýzu.

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>Parametry

- `input` <xref:System.IO.Stream>  
  Datový proud, který obsahuje data XML.

- `settings` <xref:System.Xml.XmlReaderSettings>  
  Nastavení pro novou instanci <xref:System.Xml.XmlReader>. Tato hodnota může být `null`.

- `inputContext` <xref:System.Xml.XmlParserContext>  
  Kontextové informace vyžadované k analýze fragmentu XML. Tato hodnota může být `null`.

## <a name="returns"></a>Vrací

<xref:System.Xml.XmlReader>  
Objekt, který se používá ke čtení dat XML v datovém proudu.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Metoda `XmlReader.CreateSqlReader` je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Xml>

**Sestavení:** System. XML. dll

**Verze .NET Framework:** K dispozici od verze 2,0.
