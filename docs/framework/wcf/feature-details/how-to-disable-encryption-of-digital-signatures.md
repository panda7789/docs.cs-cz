---
title: 'Postupy: Zákaz šifrování digitálních podpisů'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: 7ef305fdfd9a4ee61dfd89fdd46f2dc03a350977
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595398"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Postupy: Zákaz šifrování digitálních podpisů
Ve výchozím nastavení je zpráva podepsaná a podpis je digitálně zašifrovaný. To je řízeno vytvořením vlastní vazby s instancí <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a nastavením `MessageProtectionOrder` vlastnosti obou tříd na <xref:System.ServiceModel.Security.MessageProtectionOrder> hodnotu výčtu. Výchozí formát je <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Tento proces spotřebovává až 30 procent více času, než jednoduše přihlašujete a šifrujete na základě celkové velikosti zprávy (zmenšením zprávy, větší dopad na výkon). Zakázání šifrování podpisu ale může útočníkovi umožnit odhadnout obsah zprávy. To je možné, protože element signatura obsahuje hodnotu hash prostého textu každé podepsané části ve zprávě. I když je text zprávy ve výchozím nastavení zašifrovaný, nešifrovaný podpis obsahuje před šifrováním kód hash těla zprávy. Pokud je sada možných hodnot pro odstraněnou a šifrovanou část malá, útočník může obsah odvodit, protože si vyhledá hodnotu hash. Šifrování signatury zmírnit tento vektor útoku.  
  
 Proto zakažte šifrování signatury pouze v případě, že je hodnota obsahu nízká nebo když je množina možných hodnot obsahu velká a nedeterministické a zisk výkonu je důležitější než zmírnění výše popsaného útoku.  
  
> [!NOTE]
> Pokud není v zašifrované zprávě žádná zpráva, element signatura není zašifrovaný, i když <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> je vlastnost nebo nastavená na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> . K tomuto chování dochází i u vazeb poskytovaných systémem. všechny vazby poskytnuté systémem mají pořadí ochrany zpráv nastavené na `SignBeforeEncryptAndEncryptSignature` . Technologie WCF vygeneruje Web Services Description Language (WSDL), ale bude stále obsahovat `<sp:EncryptSignature>` kontrolní výraz.  
  
### <a name="to-disable-digital-signing"></a>Zakázání digitálního podepisování  
  
1. Vytvořte <xref:System.ServiceModel.Channels.CustomBinding> . Další informace najdete v tématu [Postup: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. Přidejte <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> do kolekce vazeb buď nebo, a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .  
  
3. Nastavte <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> nebo nastavte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> .  
  
## <a name="see-also"></a>Viz také

- [Možnosti zabezpečení u vlastních vazeb](security-capabilities-with-custom-bindings.md)
