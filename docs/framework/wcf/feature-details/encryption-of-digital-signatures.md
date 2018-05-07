---
title: Šifrování digitálních podpisů
ms.date: 03/30/2017
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
ms.openlocfilehash: 1a44e3e6110a2c03e4aa71947227485938c12180
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="encryption-of-digital-signatures"></a>Šifrování digitálních podpisů
Ve výchozím nastavení je podepsat a zašifrovat zprávu a podpis je digitálně šifrována. To můžete řídit tak, že vytvoříte vlastní vazby s instancí <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a nastavením `MessageProtectionOrder` vlastnost buď třídy <xref:System.ServiceModel.Security.MessageProtectionOrder> hodnota výčtu. Výchozí hodnota je <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Tento proces trvat 10 až 40 procent delší než jednoduše podepisování a šifrování. Zakázáním šifrování podpis, však může útočníkovi umožnit uhodnout obsah zprávy. To je možné, protože obsahuje prvek podpisu hodnota hash ve formátu prostého textu každých podepsaný části ve zprávě. Například i když text zprávy je ve výchozím nastavení zašifrované, nezašifrované podpis obsahuje kód hash textu zprávy. Pokud zpráva je malý, může útočník moci odvodit obsah. Šifrování podpis snižuje nebo eliminuje tuto možnost.  
  
 Proto zakážete šifrování podpis pouze v případě, že nízkou hodnotu obsahu, a zvýšení výkonu bude značné, například při odesílání velké binární soubory, které mají vliv na žádné zabezpečení.  
  
### <a name="to-disable-digital-signing"></a>Chcete-li zakázat digitální podpis  
  
1.  Vytvoření <xref:System.ServiceModel.Channels.CustomBinding>. Další informace najdete v tématu [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2.  Buď přidejte <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ke kolekci vazby.  
  
3.  Nastavit <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, nebo nastavte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
 Další informace o vytváření vlastních vazeb najdete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). Další informace o vytváření vlastních vazeb pro režim konkrétní ověřování najdete v tématu [postupy: vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Security.MessageProtectionOrder>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Vytváření uživatelem definovaných vazeb](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)  
 [Postupy: Vytvoření SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
