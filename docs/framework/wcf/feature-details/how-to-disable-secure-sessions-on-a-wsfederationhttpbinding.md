---
title: 'Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
ms.openlocfilehash: 810c5b127a34fb0a35e8fd2d83ff59e00aca0ba1
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972050"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="d25e5-102">Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d25e5-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>

<span data-ttu-id="d25e5-103">Některé služby můžou vyžadovat federované přihlašovací údaje, ale nepodporují zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="d25e5-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="d25e5-104">V takovém případě je nutné zakázat funkci Zabezpečená relace.</span><span class="sxs-lookup"><span data-stu-id="d25e5-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="d25e5-105">Na rozdíl od <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.WSFederationHttpBinding> , Třída neposkytuje způsob, jak zakázat zabezpečené relace při komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="d25e5-105">Unlike the <xref:System.ServiceModel.WSHttpBinding>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="d25e5-106">Místo toho je nutné vytvořit vlastní vazbu, která nahrazuje nastavení zabezpečené relace nástrojem Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="d25e5-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>

<span data-ttu-id="d25e5-107">Toto téma ukazuje, jak upravit prvky vazby obsažené v a <xref:System.ServiceModel.WSFederationHttpBinding> vytvořit vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="d25e5-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="d25e5-108">Výsledek je stejný <xref:System.ServiceModel.WSFederationHttpBinding> jako s s tím rozdílem, že nepoužívá zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="d25e5-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="d25e5-109">Vytvoření vlastní federované vazby bez zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="d25e5-109">To create a custom federated binding without secure session</span></span>

1. <span data-ttu-id="d25e5-110">Vytvořte instanci <xref:System.ServiceModel.WSFederationHttpBinding> třídy buď imperativně v kódu, nebo načtením z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d25e5-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>

2. <span data-ttu-id="d25e5-111">Naklonujte <xref:System.ServiceModel.Channels.CustomBinding>do. <xref:System.ServiceModel.WSFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d25e5-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

3. <span data-ttu-id="d25e5-112"><xref:System.ServiceModel.Channels.SecurityBindingElement> Vyhledejte<xref:System.ServiceModel.Channels.CustomBinding>v.</span><span class="sxs-lookup"><span data-stu-id="d25e5-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

4. <span data-ttu-id="d25e5-113"><xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> Vyhledejte<xref:System.ServiceModel.Channels.SecurityBindingElement>v.</span><span class="sxs-lookup"><span data-stu-id="d25e5-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>

5. <span data-ttu-id="d25e5-114">Nahraďte původní <xref:System.ServiceModel.Channels.SecurityBindingElement> elementem vazby zabezpečení Bootstrap <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>z.</span><span class="sxs-lookup"><span data-stu-id="d25e5-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>

## <a name="example"></a><span data-ttu-id="d25e5-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="d25e5-115">Example</span></span>

<span data-ttu-id="d25e5-116">Následující příklad vytvoří vlastní federované vazby bez zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="d25e5-116">This following example creates a custom federated binding without secure session.</span></span>

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="d25e5-117">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d25e5-117">Compiling the Code</span></span>

- <span data-ttu-id="d25e5-118">Chcete-li zkompilovat příklad kódu, vytvořte projekt, který odkazuje na sestavení System. ServiceModel. dll.</span><span class="sxs-lookup"><span data-stu-id="d25e5-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="d25e5-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d25e5-119">See also</span></span>

- [<span data-ttu-id="d25e5-120">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d25e5-120">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
