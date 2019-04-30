---
title: Šifrování digitálních podpisů
ms.date: 03/30/2017
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
ms.openlocfilehash: ea53a575802f1e7903a66c2eda466c8937fb02f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856393"
---
# <a name="encryption-of-digital-signatures"></a>Šifrování digitálních podpisů
Ve výchozím nastavení zprávy je podepsaný a zašifrovaný a digitálně podpis zašifrují. To můžete řídit tak, že vytvoříte vlastní vazby s instancí <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a nastavení `MessageProtectionOrder` vlastnost buď třídy <xref:System.ServiceModel.Security.MessageProtectionOrder> hodnota výčtu. Výchozí hodnota je <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Tento proces trvá déle, než jednoduše podepisování a šifrování 10 až 40 procent. Zakázáním šifrování podpisu, ale může umožnit útočníkovi možnost uhádnout obsah zprávy. Je to možné, proto prvek podpisu obsahuje kód hash ve formátu prostého textu každý podepsaný části ve zprávě. Například i když obsah zprávy se šifrují ve výchozím nastavení, nešifrované podpis obsahuje kód hash těla zprávy. Pokud má zpráva malé, může útočník moct odvodit obsah. Šifrování podpis snižuje nebo eliminuje tuto možnost.  
  
 Proto se zakážete šifrování podpisu pouze v případě, že je hodnota obsah s nízkou, a zvýšení výkonu bude významný, například při odesílání velkých binárních souborů, které mají vliv na žádné zabezpečení.  
  
### <a name="to-disable-digital-signing"></a>Chcete-li zakázat digitální podpis  
  
1. Vytvoření <xref:System.ServiceModel.Channels.CustomBinding>. Další informace najdete v tématu [jak: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. Buď přidejte <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ke kolekci vazby.  
  
3. Nastavte <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, nebo nastavte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
 Další informace o vytváření vlastních vazeb naleznete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). Další informace o vytvoření vlastní vazby pro režim konkrétní ověřování najdete v části [jak: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Security.MessageProtectionOrder>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- [Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Vytváření uživatelem definovaných vazeb](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
- [Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
