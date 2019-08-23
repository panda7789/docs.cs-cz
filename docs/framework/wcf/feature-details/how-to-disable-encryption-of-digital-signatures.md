---
title: 'Postupy: Zákaz šifrování digitálních podpisů'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: 461c5af2c7fbb98486a8decbe4aa998d8d21070d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911181"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Postupy: Zákaz šifrování digitálních podpisů
Ve výchozím nastavení je zpráva podepsaná a podpis je digitálně zašifrovaný. To je řízeno vytvořením vlastní vazby s instancí <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> nebo a nastavením `MessageProtectionOrder` vlastnosti obou tříd na <xref:System.ServiceModel.Security.MessageProtectionOrder> hodnotu výčtu. Výchozí hodnota je <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Tento proces spotřebovává až 30 procent více času, než jednoduše přihlašujete a šifrujete na základě celkové velikosti zprávy (zmenšením zprávy, větší dopad na výkon). Zakázání šifrování podpisu ale může útočníkovi umožnit odhadnout obsah zprávy. To je možné, protože element signatura obsahuje hodnotu hash prostého textu každé podepsané části ve zprávě. I když je text zprávy ve výchozím nastavení zašifrovaný, nešifrovaný podpis obsahuje před šifrováním kód hash těla zprávy. Pokud je sada možných hodnot pro odstraněnou a šifrovanou část malá, útočník může obsah odvodit, protože si vyhledá hodnotu hash. Šifrování signatury zmírnit tento vektor útoku.  
  
 Proto zakažte šifrování signatury pouze v případě, že je hodnota obsahu nízká nebo když je množina možných hodnot obsahu velká a nedeterministické a zisk výkonu je důležitější než zmírnění výše popsaného útoku.  
  
> [!NOTE]
> Pokud není v zašifrované zprávě žádná zpráva, element signatura není zašifrovaný, i když <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> je vlastnost nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> nastavená na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. K tomuto chování dochází i u vazeb poskytovaných systémem. všechny vazby poskytnuté systémem mají pořadí ochrany zpráv nastavené na `SignBeforeEncryptAndEncryptSignature`. Technologie WCF vygeneruje Web Services Description Language (WSDL), ale bude stále obsahovat `<sp:EncryptSignature>` kontrolní výraz.  
  
### <a name="to-disable-digital-signing"></a>Zakázání digitálního podepisování  
  
1. Vytvoření <xref:System.ServiceModel.Channels.CustomBinding>. Další informace najdete v tématu [jak: Vytvořte vlastní vazbu pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. Přidejte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> do kolekce <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> vazeb buď nebo, a.  
  
3. Nastavte vlastnost na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>nebo nastavte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Viz také:

- [Možnosti zabezpečení u vlastních vazeb](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
