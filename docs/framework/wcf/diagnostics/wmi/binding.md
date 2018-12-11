---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 84e304f3dedcbd785d6238e6cb5eb142c288b995
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149702"
---
# <a name="binding"></a>Vazba
rozhraní WMI vazby  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
 Třídy vazby nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třídy vazby má následující vlastnosti.  
  
### <a name="bindingelements"></a>Třídy BindingElements  
 Datový typ: Pole BindingElement  
  
 Typ přístupu: jen pro čtení  
  
 Kolekce elementů, které jsou implementovány vazbou vazby.  
  
### <a name="closetimeout"></a>closeTimeout  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Časový interval poskytnutý pro dokončení operace uzavření.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Název vazby.  
  
### <a name="namespace"></a>Obor názvů  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 XML obor názvů vazby.  
  
### <a name="opentimeout"></a>openTimeout  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Časový interval poskytnutý pro dokončení operace otevření.  
  
### <a name="receivetimeout"></a>receiveTimeout  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Časový interval poskytnutý pro dokončení operace obdržení.  
  
### <a name="scheme"></a>Schéma  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Schéma přepravy identifikátoru URI, který je používán továren kanálu a posluchače, které jsou vytvořeny vazbou.  
  
### <a name="sendtimeout"></a>SendTimeout  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Časový interval poskytnutý pro dokončení operace odeslání.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.Binding>
