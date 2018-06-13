---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: 78914d52a9e57fe2e48adcfc0d7b6f911a0d8b3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487825"
---
# <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas
XmlDictionaryReaderQuotas  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Třída XmlDictionaryReaderQuotas, který nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída XmlDictionaryReaderQuotas, který má následující vlastnosti:  
  
### <a name="maxarraylength"></a>MaxArrayLength  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální povolená délka pole.  
  
### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální povolená bajtů vrácených pro každý pro čtení.  
  
### <a name="maxdepth"></a>MaxDepth  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální hloubka vnořeného uzlu pro každý pro čtení.  
  
### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet znaků v názvu tabulky povolené.  
  
### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet znaků v obsahu elementu XML povolen.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
