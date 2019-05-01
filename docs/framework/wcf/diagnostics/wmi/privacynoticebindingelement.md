---
title: PrivacyNoticeBindingElement
ms.date: 03/30/2017
ms.assetid: 0cf110b1-e25b-4d67-986b-10cb04dc4826
ms.openlocfilehash: 04c65d0aa589d99766b4ffc8f1550036d2880718
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962960"
---
# <a name="privacynoticebindingelement"></a>PrivacyNoticeBindingElement
PrivacyNoticeBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class PrivacyNoticeBindingElement : BindingElement  
{  
  sint32 PrivacyNoticeVersion;  
  string Url;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída PrivacyNoticeBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída PrivacyNoticeBindingElement má následující vlastnosti:  
  
### <a name="privacynoticeversion"></a>PrivacyNoticeVersion  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Verze oznámení soukromí.  
  
### <a name="url"></a>Adresa URL  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Adresa URL, na které je umístěno oznámení soukromí.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
