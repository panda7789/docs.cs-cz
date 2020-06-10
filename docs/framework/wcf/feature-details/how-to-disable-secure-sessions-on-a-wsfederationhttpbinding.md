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
ms.openlocfilehash: df057d64feb89d1e43b938b36cb48f2f103b17d0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595385"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="f2163-102">Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f2163-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>

<span data-ttu-id="f2163-103">Některé služby můžou vyžadovat federované přihlašovací údaje, ale nepodporují zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="f2163-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="f2163-104">V takovém případě je nutné zakázat funkci Zabezpečená relace.</span><span class="sxs-lookup"><span data-stu-id="f2163-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="f2163-105">Na rozdíl od <xref:System.ServiceModel.WSHttpBinding> , <xref:System.ServiceModel.WSFederationHttpBinding> Třída neposkytuje způsob, jak zakázat zabezpečené relace při komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="f2163-105">Unlike the <xref:System.ServiceModel.WSHttpBinding>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="f2163-106">Místo toho je nutné vytvořit vlastní vazbu, která nahrazuje nastavení zabezpečené relace nástrojem Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="f2163-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>

<span data-ttu-id="f2163-107">Toto téma ukazuje, jak upravit prvky vazby obsažené v a <xref:System.ServiceModel.WSFederationHttpBinding> vytvořit vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="f2163-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="f2163-108">Výsledek je stejný jako s <xref:System.ServiceModel.WSFederationHttpBinding> s tím rozdílem, že nepoužívá zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="f2163-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="f2163-109">Vytvoření vlastní federované vazby bez zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="f2163-109">To create a custom federated binding without secure session</span></span>

1. <span data-ttu-id="f2163-110">Vytvořte instanci <xref:System.ServiceModel.WSFederationHttpBinding> třídy buď imperativně v kódu, nebo načtením z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="f2163-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>

2. <span data-ttu-id="f2163-111">Naklonujte <xref:System.ServiceModel.WSFederationHttpBinding> do <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="f2163-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

3. <span data-ttu-id="f2163-112">Vyhledejte <xref:System.ServiceModel.Channels.SecurityBindingElement> v <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="f2163-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

4. <span data-ttu-id="f2163-113">Vyhledejte <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> v <xref:System.ServiceModel.Channels.SecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="f2163-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>

5. <span data-ttu-id="f2163-114">Nahraďte původní <xref:System.ServiceModel.Channels.SecurityBindingElement> elementem vazby zabezpečení Bootstrap z <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> .</span><span class="sxs-lookup"><span data-stu-id="f2163-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>

## <a name="example"></a><span data-ttu-id="f2163-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2163-115">Example</span></span>

<span data-ttu-id="f2163-116">Následující příklad vytvoří vlastní federované vazby bez zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="f2163-116">This following example creates a custom federated binding without secure session.</span></span>

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="f2163-117">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f2163-117">Compiling the Code</span></span>

- <span data-ttu-id="f2163-118">Chcete-li zkompilovat příklad kódu, vytvořte projekt, který odkazuje na sestavení System. ServiceModel. dll.</span><span class="sxs-lookup"><span data-stu-id="f2163-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2163-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2163-119">See also</span></span>

- [<span data-ttu-id="f2163-120">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f2163-120">Bindings and Security</span></span>](bindings-and-security.md)
