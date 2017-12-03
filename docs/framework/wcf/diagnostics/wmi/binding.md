---
title: Binding2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9e44d161e1229db9145f4ed7e337396bbd98c68
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="binding"></a>Vazba
rozhraní WMI vazby  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třídu vazby nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třídu vazby má následující vlastnosti.  
  
### <a name="bindingelements"></a>Třídy BindingElements  
 Datový typ: pole BindingElement  
  
 Přístup k typu: jen pro čtení  
  
 Kolekce elementů vazby implementované vazby.  
  
### <a name="closetimeout"></a>Intervalu  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Interval čas zadaný pro dokončení operace uzavření.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Název vazby.  
  
### <a name="namespace"></a>Obor názvů  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Obor názvů XML vazby.  
  
### <a name="opentimeout"></a>openTimeout  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Interval čas zadaný pro otevřete na dokončení operace.  
  
### <a name="receivetimeout"></a>receiveTimeout  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Interval čas zadaný pro na dokončení operace příjmu.  
  
### <a name="scheme"></a>Schéma  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Přenosové schéma identifikátoru URI používaný kanál a naslouchací proces objekty Factory, které jsou vytvořené pomocí vazby.  
  
### <a name="sendtimeout"></a>sendTimeout  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Interval čas zadaný pro dokončení operace odeslání.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.Binding>
