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
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding
Některé služby mohou vyžadovat federované přihlašovací údaje, ale nepodporuje zabezpečených relací. V takovém případě je třeba zakázat funkci zabezpečené relace. Na rozdíl od <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, <xref:System.ServiceModel.WSFederationHttpBinding> třída neposkytuje způsob, jak zakázat zabezpečených relací při komunikaci se službou. Místo toho musíte vytvořit vlastní vazby, který nahradí bootstrap nastavení zabezpečené relace.  
  
 Toto téma ukazuje, jak upravit elementů vazby obsažená v rámci <xref:System.ServiceModel.WSFederationHttpBinding> k vytvoření vlastní vazby. Výsledkem je stejný jako <xref:System.ServiceModel.WSFederationHttpBinding> s tím rozdílem, že nepoužívá zabezpečených relací.  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a>Chcete-li vytvořit vlastní federované vazby bez zabezpečené relace  
  
1.  Vytvoření instance <xref:System.ServiceModel.WSFederationHttpBinding> třídy imperativní v kódu nebo načtením jeden z konfiguračního souboru.  
  
2.  Klon <xref:System.ServiceModel.WSFederationHttpBinding> do <xref:System.ServiceModel.Channels.CustomBinding>.  
  
3.  Najít <xref:System.ServiceModel.Channels.SecurityBindingElement> v <xref:System.ServiceModel.Channels.CustomBinding>.  
  
4.  Najít <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> v <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
5.  Nahradí původní <xref:System.ServiceModel.Channels.SecurityBindingElement> s elementem vazby bootstrap zabezpečení z <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.  
  
## <a name="example"></a>Příklad  
 Tento následující příklad vytvoří vlastní federované vazby bez zabezpečené relace.  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Kompilace příkladu kódu, vytvořte projekt, který odkazuje na sestavení System.ServiceModel.dll.  
  
## <a name="see-also"></a>Viz také  
 [Vazby a zabezpečení](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
