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
ms.openlocfilehash: b61c8935b785a80f6e3163b3bafd83d3dd84f52f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202078"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding
Některé služby může vyžadovat federované přihlašovací údaje, ale nepodporuje zabezpečených relací. V takovém případě je nutné zakázat funkci zabezpečenou relaci. Na rozdíl od <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding> třída neposkytuje způsob, jak zakázání zabezpečených relací při komunikaci se službou. Místo toho musíte vytvořit vlastní vazby, který nahradí nastavení zabezpečenou relaci bootstrap.  
  
 Toto téma ukazuje, jak upravit elementů vazby obsažená v rámci <xref:System.ServiceModel.WSFederationHttpBinding> k vytvoření vlastní vazby. Výsledek je stejný jako <xref:System.ServiceModel.WSFederationHttpBinding> s tím rozdílem, že ho nepoužívá zabezpečených relací.  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a>Můžete vytvořit vlastní federované vazby bez zabezpečené relace  
  
1.  Vytvoření instance <xref:System.ServiceModel.WSFederationHttpBinding> třídy imperativně v kódu nebo načtením jeden z konfiguračního souboru.  
  
2.  Klonování <xref:System.ServiceModel.WSFederationHttpBinding> do <xref:System.ServiceModel.Channels.CustomBinding>.  
  
3.  Najít <xref:System.ServiceModel.Channels.SecurityBindingElement> v <xref:System.ServiceModel.Channels.CustomBinding>.  
  
4.  Najít <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> v <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
5.  Ten původní nahradí <xref:System.ServiceModel.Channels.SecurityBindingElement> s element vazby zabezpečení samozavádění z <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří vlastní federované vazby bez zabezpečenou relaci.  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Příklad kódu zkompilovat, vytvořte projekt aplikace a odkazuje na sestavení System.ServiceModel.dll.  
  
## <a name="see-also"></a>Viz také  
 [Vazby a zabezpečení](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
