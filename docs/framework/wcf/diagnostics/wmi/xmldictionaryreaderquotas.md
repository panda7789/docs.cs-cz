---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: 9bc519509b00383be333ac605688950d2709117c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199471"
---
# <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas
XmlDictionaryReaderQuotas  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třídu XmlDictionaryReaderQuotas, který nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třídu XmlDictionaryReaderQuotas, který má následující vlastnosti:  
  
### <a name="maxarraylength"></a>MaxArrayLength  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální povolená délka pole.  
  
### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální povolené bajty vrácené na při každém čtení.  
  
### <a name="maxdepth"></a>MaxDepth  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální hloubku vnořeného uzlu při každém čtení.  
  
### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximum znaků povolených v názvu tabulky.  
  
### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximum znaků povolených v obsahu prvku XML.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
