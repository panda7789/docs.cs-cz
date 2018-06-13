---
title: PrivacyNoticeBindingElement
ms.date: 03/30/2017
ms.assetid: 0cf110b1-e25b-4d67-986b-10cb04dc4826
ms.openlocfilehash: a4ae5153525d5468955a09d19e534c00114c6530
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485115"
---
# <a name="privacynoticebindingelement"></a>PrivacyNoticeBindingElement
PrivacyNoticeBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
 Přístup k typu: jen pro čtení  
  
 Verze oznámení o ochraně osobních údajů.  
  
### <a name="url"></a>Adresa URL  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Adresa URL, ve kterém se nachází v oznámení o ochraně osobních údajů.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
