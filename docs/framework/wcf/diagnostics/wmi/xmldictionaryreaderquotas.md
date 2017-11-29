---
title: XmlDictionaryReaderQuotas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 980a7eacd095dc1b601d63f5a807f2e287c09885
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
