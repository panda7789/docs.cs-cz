---
title: Šifrování digitálních podpisů
ms.date: 03/30/2017
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
ms.openlocfilehash: 41094b2eee50e97cf60887cfa29f8110f2895bfa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597394"
---
# <a name="encryption-of-digital-signatures"></a>Šifrování digitálních podpisů
Ve výchozím nastavení je zpráva podepsaná a šifrovaná a podpis je digitálně zašifrovaný. Můžete to řídit vytvořením vlastní vazby s instancí <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a pak nastavením `MessageProtectionOrder` vlastnosti obou tříd na <xref:System.ServiceModel.Security.MessageProtectionOrder> hodnotu výčtu. Výchozí formát je <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Tento proces trvá 10 až 40% déle než pouhým přihlášením a šifrováním. Zakázání šifrování podpisu ale může útočníkovi umožnit odhadnout obsah zprávy. To je možné, protože element signatura obsahuje hodnotu hash prostého textu každé podepsané části ve zprávě. I když je text zprávy ve výchozím nastavení zašifrovaný, nešifrovaný podpis obsahuje kód hash těla zprávy. Pokud je zpráva malá, útočník může obsah odvodit. Šifrování signatury snižuje nebo eliminuje tuto možnost.  
  
 Proto zakažte šifrování signatury pouze v případě, že je hodnota obsahu nízká a zisk výkonu bude významný, například při posílání velkých binárních souborů, které nemají žádné důsledky zabezpečení.  
  
### <a name="to-disable-digital-signing"></a>Zakázání digitálního podepisování  
  
1. Vytvořte <xref:System.ServiceModel.Channels.CustomBinding> . Další informace najdete v tématu [Postup: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. Přidejte <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> do kolekce vazeb buď nebo, a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .  
  
3. Nastavte <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> nebo nastavte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> .  
  
 Další informace o vytváření vlastních vazeb naleznete v tématu [vytváření uživatelsky definovaných vazeb](../extending/creating-user-defined-bindings.md). Další informace o vytvoření vlastní vazby pro konkrétní režim ověřování naleznete v tématu [How to: Create a SecurityBindingElement for a Authentication Mode](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Security.MessageProtectionOrder>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Vytváření uživatelem definovaných vazeb](../extending/creating-user-defined-bindings.md)
- [Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
