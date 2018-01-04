---
title: "Šifrování digitálních podpisů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 541e8a60797dca5db632ad8bd383cf926ec0d6dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="encryption-of-digital-signatures"></a><span data-ttu-id="19cdb-102">Šifrování digitálních podpisů</span><span class="sxs-lookup"><span data-stu-id="19cdb-102">Encryption of Digital Signatures</span></span>
<span data-ttu-id="19cdb-103">Ve výchozím nastavení je podepsat a zašifrovat zprávu a podpis je digitálně šifrována.</span><span class="sxs-lookup"><span data-stu-id="19cdb-103">By default, a message is signed and encrypted, and the signature is digitally encrypted.</span></span> <span data-ttu-id="19cdb-104">To můžete řídit tak, že vytvoříte vlastní vazby s instancí <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a nastavením `MessageProtectionOrder` vlastnost buď třídy <xref:System.ServiceModel.Security.MessageProtectionOrder> hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="19cdb-104">You can control this by creating a custom binding with an instance of the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> or the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and then setting the `MessageProtectionOrder` property of either class to a <xref:System.ServiceModel.Security.MessageProtectionOrder> enumeration value.</span></span> <span data-ttu-id="19cdb-105">Výchozí hodnota je <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>.</span><span class="sxs-lookup"><span data-stu-id="19cdb-105">The default is <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>.</span></span> <span data-ttu-id="19cdb-106">Tento proces trvat 10 až 40 procent delší než jednoduše podepisování a šifrování.</span><span class="sxs-lookup"><span data-stu-id="19cdb-106">This process takes 10 to 40 percent longer than simply signing and encrypting.</span></span> <span data-ttu-id="19cdb-107">Zakázáním šifrování podpis, však může útočníkovi umožnit uhodnout obsah zprávy.</span><span class="sxs-lookup"><span data-stu-id="19cdb-107">Disabling encryption of the signature, however, might allow an attacker to guess the contents of the message.</span></span> <span data-ttu-id="19cdb-108">To je možné, protože obsahuje prvek podpisu hodnota hash ve formátu prostého textu každých podepsaný části ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="19cdb-108">This is possible because the signature element contains the hash code of the plain text of every signed part in the message.</span></span> <span data-ttu-id="19cdb-109">Například i když text zprávy je ve výchozím nastavení zašifrované, nezašifrované podpis obsahuje kód hash textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="19cdb-109">For example, although the message body is encrypted by default, the unencrypted signature contains the hash code of the message body.</span></span> <span data-ttu-id="19cdb-110">Pokud zpráva je malý, může útočník moci odvodit obsah.</span><span class="sxs-lookup"><span data-stu-id="19cdb-110">If the message is small, an attacker might be able to deduce the contents.</span></span> <span data-ttu-id="19cdb-111">Šifrování podpis snižuje nebo eliminuje tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="19cdb-111">Encrypting the signature reduces or eliminates this possibility.</span></span>  
  
 <span data-ttu-id="19cdb-112">Proto zakážete šifrování podpis pouze v případě, že nízkou hodnotu obsahu, a zvýšení výkonu bude značné, například při odesílání velké binární soubory, které mají vliv na žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="19cdb-112">Therefore, disable encryption of the signature only when the value of the content is low, and the performance gain will be significant, for example, when sending large binary files that have no security implications.</span></span>  
  
### <a name="to-disable-digital-signing"></a><span data-ttu-id="19cdb-113">Chcete-li zakázat digitální podpis</span><span class="sxs-lookup"><span data-stu-id="19cdb-113">To disable digital signing</span></span>  
  
1.  <span data-ttu-id="19cdb-114">Vytvoření <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="19cdb-114">Create a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="19cdb-115">[Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="19cdb-115"> [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
2.  <span data-ttu-id="19cdb-116">Buď přidejte <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ke kolekci vazby.</span><span class="sxs-lookup"><span data-stu-id="19cdb-116">Add either an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> or a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> to the binding collection.</span></span>  
  
3.  <span data-ttu-id="19cdb-117">Nastavit <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, nebo nastavte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.</span><span class="sxs-lookup"><span data-stu-id="19cdb-117">Set the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> property to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, or set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> property to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="19cdb-118">vytváření vlastních vazeb, najdete v části [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="19cdb-118"> creating custom bindings, see [Creating User-Defined Bindings](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="19cdb-119">Vytvoření vlastní vazby pro konkrétní ověřování režimu, najdete v části [postupy: vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).</span><span class="sxs-lookup"><span data-stu-id="19cdb-119"> creating a custom binding for a specific authentication mode, see [How to: Create a SecurityBindingElement for a Specified Authentication Mode](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19cdb-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="19cdb-120">See Also</span></span>  
 <xref:System.ServiceModel.Security.MessageProtectionOrder>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 [<span data-ttu-id="19cdb-121">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="19cdb-121">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="19cdb-122">Vytváření uživatelem definovaných vazeb</span><span class="sxs-lookup"><span data-stu-id="19cdb-122">Creating User-Defined Bindings</span></span>](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)  
 [<span data-ttu-id="19cdb-123">Postupy: Vytvoření SecurityBindingElement pro zadaný režim ověřování</span><span class="sxs-lookup"><span data-stu-id="19cdb-123">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
