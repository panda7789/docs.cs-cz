---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: f7c4e30b72af36de1d3088e4ca8cd98ced734104
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692321"
---
# <a name="securitybindingelement"></a>SecurityBindingElement
SecurityBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída SecurityBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída SecurityBindingElement má následující vlastnosti:  
  
### <a name="defaultalgorithmsuite"></a>DefaultAlgorithmSuite  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Určuje algoritmy, které mají být použity s vazbou.  
  
### <a name="includetimestamp"></a>IncludeTimestamp  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Logická hodnota určující, zda každá zpráva obsahuje časovou známku.  
  
### <a name="keyentropymode"></a>KeyEntropyMode  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Zdroj šifry použitý k vytvoření klíče.  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  
 Datový typ: LocalServiceSecuritySettings  
  
 Typ přístupu: jen pro čtení  
  
 Specifické vlastnosti zabezpečení vazby pro lokální službu.  
  
### <a name="messagesecurityversion"></a>MessageSecurityVersion  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Verze použitá pro zabezpečení zprávy.  
  
### <a name="securityheaderlayout"></a>SecurityHeaderLayout  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Pořadí prvků v záhlaví zabezpečení pro tuto vazbu.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
