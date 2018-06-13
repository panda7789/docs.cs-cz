---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 0260b75a0f49e0f6f72d7d1eda642d0a494d2892
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487004"
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
