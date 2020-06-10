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
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding

Některé služby můžou vyžadovat federované přihlašovací údaje, ale nepodporují zabezpečené relace. V takovém případě je nutné zakázat funkci Zabezpečená relace. Na rozdíl od <xref:System.ServiceModel.WSHttpBinding> , <xref:System.ServiceModel.WSFederationHttpBinding> Třída neposkytuje způsob, jak zakázat zabezpečené relace při komunikaci se službou. Místo toho je nutné vytvořit vlastní vazbu, která nahrazuje nastavení zabezpečené relace nástrojem Bootstrap.

Toto téma ukazuje, jak upravit prvky vazby obsažené v a <xref:System.ServiceModel.WSFederationHttpBinding> vytvořit vlastní vazbu. Výsledek je stejný jako s <xref:System.ServiceModel.WSFederationHttpBinding> s tím rozdílem, že nepoužívá zabezpečené relace.

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a>Vytvoření vlastní federované vazby bez zabezpečené relace

1. Vytvořte instanci <xref:System.ServiceModel.WSFederationHttpBinding> třídy buď imperativně v kódu, nebo načtením z konfiguračního souboru.

2. Naklonujte <xref:System.ServiceModel.WSFederationHttpBinding> do <xref:System.ServiceModel.Channels.CustomBinding> .

3. Vyhledejte <xref:System.ServiceModel.Channels.SecurityBindingElement> v <xref:System.ServiceModel.Channels.CustomBinding> .

4. Vyhledejte <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> v <xref:System.ServiceModel.Channels.SecurityBindingElement> .

5. Nahraďte původní <xref:System.ServiceModel.Channels.SecurityBindingElement> elementem vazby zabezpečení Bootstrap z <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> .

## <a name="example"></a>Příklad

Následující příklad vytvoří vlastní federované vazby bez zabezpečené relace.

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

- Chcete-li zkompilovat příklad kódu, vytvořte projekt, který odkazuje na sestavení System. ServiceModel. dll.

## <a name="see-also"></a>Viz také

- [Vazby a zabezpečení](bindings-and-security.md)
