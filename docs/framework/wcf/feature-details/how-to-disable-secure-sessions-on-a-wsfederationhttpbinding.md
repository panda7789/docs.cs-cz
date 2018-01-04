---
title: "Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
caps.latest.revision: "16"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5fc5ddd1b84bf723901e449bf1bfda6a31ad1cea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="74069-102">Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="74069-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>
<span data-ttu-id="74069-103">Některé služby mohou vyžadovat federované přihlašovací údaje, ale nepodporuje zabezpečených relací.</span><span class="sxs-lookup"><span data-stu-id="74069-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="74069-104">V takovém případě je třeba zakázat funkci zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="74069-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="74069-105">Na rozdíl od <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, <xref:System.ServiceModel.WSFederationHttpBinding> třída neposkytuje způsob, jak zakázat zabezpečených relací při komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="74069-105">Unlike the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="74069-106">Místo toho musíte vytvořit vlastní vazby, který nahradí bootstrap nastavení zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="74069-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>  
  
 <span data-ttu-id="74069-107">Toto téma ukazuje, jak upravit elementů vazby obsažená v rámci <xref:System.ServiceModel.WSFederationHttpBinding> k vytvoření vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="74069-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="74069-108">Výsledkem je stejný jako <xref:System.ServiceModel.WSFederationHttpBinding> s tím rozdílem, že nepoužívá zabezpečených relací.</span><span class="sxs-lookup"><span data-stu-id="74069-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="74069-109">Chcete-li vytvořit vlastní federované vazby bez zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="74069-109">To create a custom federated binding without secure session</span></span>  
  
1.  <span data-ttu-id="74069-110">Vytvoření instance <xref:System.ServiceModel.WSFederationHttpBinding> třídy imperativní v kódu nebo načtením jeden z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="74069-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>  
  
2.  <span data-ttu-id="74069-111">Klon <xref:System.ServiceModel.WSFederationHttpBinding> do <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="74069-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
3.  <span data-ttu-id="74069-112">Najít <xref:System.ServiceModel.Channels.SecurityBindingElement> v <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="74069-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
4.  <span data-ttu-id="74069-113">Najít <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> v <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="74069-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
5.  <span data-ttu-id="74069-114">Nahradí původní <xref:System.ServiceModel.Channels.SecurityBindingElement> s elementem vazby bootstrap zabezpečení z <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="74069-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74069-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="74069-115">Example</span></span>  
 <span data-ttu-id="74069-116">Tento následující příklad vytvoří vlastní federované vazby bez zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="74069-116">This following example creates a custom federated binding without secure session.</span></span>  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="74069-117">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="74069-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="74069-118">Kompilace příkladu kódu, vytvořte projekt, který odkazuje na sestavení System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="74069-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74069-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="74069-119">See Also</span></span>  
 [<span data-ttu-id="74069-120">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="74069-120">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
