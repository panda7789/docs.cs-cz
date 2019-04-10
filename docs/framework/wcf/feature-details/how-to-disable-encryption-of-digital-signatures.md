---
title: 'Postupy: Zákaz šifrování digitálních podpisů'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: e2fd2a058e636ebf398f9d0c71a93788ccd7dfa0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59325264"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Postupy: Zákaz šifrování digitálních podpisů
Ve výchozím nastavení zprávy je podepsaná a digitálně podpis zašifrují. Toto se řídí vytváření vlastní vazby s instancí <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a nastavení `MessageProtectionOrder` vlastnost buď třídy <xref:System.ServiceModel.Security.MessageProtectionOrder> hodnota výčtu. Výchozí hodnota je <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Tento proces využívá až 30 procent déle než jednoduše podepisování a šifrování založené na celkovou velikost zprávy (Čím menší zprávy, tím větší dopad na výkon). Zakázáním šifrování podpisu, ale může umožnit útočníkovi možnost uhádnout obsah zprávy. Je to možné, proto prvek podpisu obsahuje kód hash ve formátu prostého textu každý podepsaný části ve zprávě. Například i když obsah zprávy se šifrují ve výchozím nastavení, nešifrované podpis obsahuje kód hash před šifrování těla zprávy. Pokud sadu možných hodnot pro část šifrovaný a podepsaný držitelem je nízká, útočník může být možné odvodit obsah podle hodnoty hash. Šifrování podpis zmírňuje tohoto útoku.  
  
 Proto zákaz šifrování podpis, pouze pokud je hodnota obsah s nízkou nebo sadu možných hodnot obsahu je Nedeterministický i velké a výkonový zisk plynoucí je mnohem důležitější než zmírnění útoků popsané výše.  
  
> [!NOTE]
>  Pokud není nic ve zprávě, která je zašifrovaná, prvek podpisu není zašifrovaný, i když <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> je nastavena na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. K tomuto chování dochází i s vazeb poskytovaných systémem; všechny vazby poskytované systémem mají pořadí ochrany zprávy, nastavte na `SignBeforeEncryptAndEncryptSignature`. Ale na webové služby WSDL (Description Language) WCF vygeneruje se pořád neobsahuje `<sp:EncryptSignature>` kontrolní výraz.  
  
### <a name="to-disable-digital-signing"></a>Chcete-li zakázat digitální podpis  
  
1. Vytvoření <xref:System.ServiceModel.Channels.CustomBinding>. Další informace najdete v tématu [jak: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. Buď přidejte <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ke kolekci vazby.  
  
3. Nastavte <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, nebo nastavte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti zabezpečení u vlastních vazeb](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
