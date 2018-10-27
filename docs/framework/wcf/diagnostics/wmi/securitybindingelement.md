---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: 601e3fafd9aa876186b7f78dfdcb87a2336ddfcd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185768"
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
  
 Přístup k typu: jen pro čtení  
  
 Určuje algoritmy, které mají být použity s vazbou.  
  
### <a name="includetimestamp"></a>IncludeTimestamp  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota určující, zda každá zpráva obsahuje časovou známku.  
  
### <a name="keyentropymode"></a>KeyEntropyMode  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Zdroj šifry použitý k vytvoření klíče.  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  
 Datový typ: LocalServiceSecuritySettings  
  
 Přístup k typu: jen pro čtení  
  
 Specifické vlastnosti zabezpečení vazby pro lokální službu.  
  
### <a name="messagesecurityversion"></a>MessageSecurityVersion  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Verze použitá pro zabezpečení zprávy.  
  
### <a name="securityheaderlayout"></a>SecurityHeaderLayout  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Pořadí prvků v záhlaví zabezpečení pro tuto vazbu.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
