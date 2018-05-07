---
title: 'Postupy: Zakázání šifrování digitálních podpisů'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: 074a32f6a69f8353568e76c99f4b65aece813f55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Postupy: Zakázání šifrování digitálních podpisů
Ve výchozím nastavení je podepsaný zprávu a podpis je digitálně zašifrovaný. Toto se řídí vytváření vlastní vazby s instancí <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a nastavení `MessageProtectionOrder` vlastnost buď třídy <xref:System.ServiceModel.Security.MessageProtectionOrder> hodnota výčtu. Výchozí hodnota je <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Tento proces využívá až o 30 procent déle než jednoduše podepisování a šifrování založené na celkovou velikost zprávy (menší zprávy, tím větší dopad na výkon). Zakázáním šifrování podpis, však může útočníkovi umožnit uhodnout obsah zprávy. To je možné, protože obsahuje prvek podpisu hodnota hash ve formátu prostého textu každých podepsaný části ve zprávě. Například i když text zprávy je ve výchozím nastavení zašifrované, nezašifrované podpis obsahuje kód hash těla zprávy před šifrování. Pokud je sada možných hodnot pro část podepsaná a šifrované malé, může útočník moci odvodit obsah pohledem na hodnotě hash. Šifrování podpis snižuje tento vektor útoku.  
  
 Proto zakážete šifrování podpis jenom v případě, že je nízkou hodnotu obsahu nebo sada možných hodnot obsahu je velké a deterministický a zvýšení výkonu je důležitější než zmírnění útoku popsané výše.  
  
> [!NOTE]
>  Pokud není co zprávy, která je zašifrovaná, nebude zašifrován prvek podpisu, i když <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> je nastavena na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. K tomuto chování dochází i s vazby poskytované systémem; všechny vazby poskytované systémem mít pořadí ochrany zprávy nastavena na `SignBeforeEncryptAndEncryptSignature`. Ale webové služby popis Language (WSDL) WCF generuje bude dál zahrnovat `<sp:EncryptSignature>` kontrolní výraz.  
  
### <a name="to-disable-digital-signing"></a>Chcete-li zakázat digitální podpis  
  
1.  Vytvoření <xref:System.ServiceModel.Channels.CustomBinding>. Další informace najdete v tématu [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2.  Buď přidejte <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ke kolekci vazby.  
  
3.  Nastavit <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, nebo nastavte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti zabezpečení u vlastních vazeb](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
