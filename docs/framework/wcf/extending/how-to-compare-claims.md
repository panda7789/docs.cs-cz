---
title: "Postupy: Porovnávání deklarací"
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
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fd23edd9e390b1f2018419c3c43be8091500c929
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compare-claims"></a>Postupy: Porovnávání deklarací
Infrastruktura Identity modelu v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] se používá k provádění kontroly autorizace. Běžné úlohy jako takový je k porovnání deklarací identity v kontextu autorizace deklarací potřeba provést požadovanou akci nebo přístupu k požadovanému zdroji. Toto téma popisuje, jak má být porovnán nároky, včetně typů předdefinované a vlastní deklarace identity. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]infrastruktury modelu Identity, najdete v části [správa deklarací a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
 Porovnání deklarace identity spočívá v porovnání tři části deklarace (typ práva a prostředků) proti stejné části v jiné deklarace identity, pokud chcete zobrazit, pokud jsou stejné. Podívejte se na téma v následujícím příkladu.  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 Typ deklarace identity mají obě deklarace identity <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, napravo od <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>a prostředek řetězce "uživatel". Všechny tři části deklarace identity jsou stejné, sami deklarace identity jsou stejné.  
  
 Typy deklarací identity předdefinované jsou porovnávány pomocí <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda. Porovnání deklarace identity specifické kód používá tam, kde je to nezbytné. Například uděleno následující dva uživatele deklarace hlavní název (UPN):  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 porovnání kód <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda vrátí `true`, v případě `example\someone` identifikuje stejného uživatele domény, který "someone@example.com".  
  
 Typy vlastních deklarací identity také je možné porovnávat pomocí <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda. Však v případech, kde typ vrácený <xref:System.IdentityModel.Claims.Claim.Resource%2A> vlastnost deklarace identity je něco jiného než primitivní typ, <xref:System.IdentityModel.Claims.Claim.Equals%2A> vrátí `true` pouze v případě, že hodnoty vrácené `Resource` vlastnosti jsou stejné podle <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda. V případech, kde to není vhodná, vlastní typ vrácený `Resource` by měly přepsat vlastnost <xref:System.IdentityModel.Claims.Claim.Equals%2A> a <xref:System.Object.GetHashCode%2A> metody pro jakoukoli vlastní zpracování je nezbytné provést.  
  
### <a name="comparing-built-in-claims"></a>Porovnání předdefinované deklarace identity  
  
1.  Zadána dvě instance <xref:System.IdentityModel.Claims.Claim> třídy, použijte <xref:System.IdentityModel.Claims.Claim.Equals%2A> pro porovnání, ujistěte se, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a>Porovnání vlastní deklarace s typy primitivní prostředků  
  
1.  Pro vlastní deklarace s typy primitivní prostředků porovnání můžete provést jako integrované deklarace identity, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2.  Pro vlastní deklarace s struktura nebo typy na základě těchto prostředků, typ prostředku by měly přepsat <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda.  
  
3.  Nejdřív zkontrolujte, zda `obj` parametr `null`a pokud ano, vrátí `false`.  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4.  Další volání <xref:System.Object.ReferenceEquals%2A> a předejte `this` a `obj` jako parametry. Vrátí-li `true`, pak vrátí `true`.  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5.  Další pokus o přiřazení `obj` místní proměnné typu třídy. Pokud se to nezdaří, je odkaz `null`. V takových případech vrátit `false`.  
  
6.  Proveďte vlastní porovnání nezbytné správně porovnat aktuální deklarace identity do zadané deklarací.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje porovnání vlastní deklarace, kde prostředků deklarace identity představuje není primitivní typ.  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a>Viz také  
 [Správa deklarací a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Postupy: vytvoření vlastních deklarací identity](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
