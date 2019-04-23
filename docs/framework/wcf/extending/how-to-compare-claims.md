---
title: 'Postupy: Porovnání deklarací'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
ms.openlocfilehash: 932ad347730b35a936e040e116e5aa6af36cd3dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343308"
---
# <a name="how-to-compare-claims"></a>Postupy: Porovnání deklarací
Infrastruktura modelu Identity ve Windows Communication Foundation (WCF) se používá k provedení kontroly autorizace. V důsledku toho běžných úloh je porovnávání deklarací identity v kontextu autorizace deklarací identity potřebný k provedení požadované akce nebo přístup k požadovanému prostředku. Toto téma popisuje, jak porovnat deklarace identity, včetně typů předdefinované a vlastní deklarace identity. Další informace o infrastruktuře identit modelu najdete v tématu [správa deklarací identity a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
 Porovnání deklarace identity spočívá v porovnání tři části deklarace identity (typ a prostředků) proti stejné části v jiné deklarace identity, pokud chcete zobrazit, pokud jsou shodné. Podívejte se na téma v následujícím příkladu.  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 Obě deklarace identity mají typ deklarace identity <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, napravo od <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>a prostředek řetězce "uživatel". Protože všechny tři části deklarace identity jsou stejné, sami deklarace identity jsou si rovny.  
  
 Typy integrovaných deklarace identity jsou porovnány pomocí <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody. Porovnání deklarace identity kódu se používá v případě potřeby. Mějme například následující deklarace identity uživatele dvě hlavní název (UPN):  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 srovnávací kód v <xref:System.IdentityModel.Claims.Claim.Equals%2A> vrátí metoda `true`, předpokládá `example\someone` stejného uživatele domény, který identifikuje "someone@example.com".  
  
 Typy vlastních deklarací identity je také možné porovnat pomocí <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody. Ale v případech, kde se typ vrácený <xref:System.IdentityModel.Claims.Claim.Resource%2A> něco jiného než primitivního typu, je vlastnost deklarace identity <xref:System.IdentityModel.Claims.Claim.Equals%2A> vrátí `true` pouze v případě, že hodnoty vrácené funkcí `Resource` vlastnosti jsou stejné podle <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody. V případech, kdy to není vhodný, vlastní typ vrácených `Resource` by měly přepsat vlastnost <xref:System.IdentityModel.Claims.Claim.Equals%2A> a <xref:System.Object.GetHashCode%2A> metody k provedení jakékoli vlastní zpracování je nezbytné.  
  
### <a name="comparing-built-in-claims"></a>Porovnání integrovaných deklarací identity  
  
1. Dvě instance s ohledem <xref:System.IdentityModel.Claims.Claim> třídy, použijte <xref:System.IdentityModel.Claims.Claim.Equals%2A> k porovnání, ujistěte se, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a>Porovnání vlastní deklarace identity s prostředků primitivní typy  
  
1. U vlastních deklarací identity s prostředků primitivní typy porovnání se dá udělat jako integrované deklarace identity, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2. Pro vlastní deklarace identity s struktury nebo třídy, na základě typů prostředků, typ prostředku by měl přepsat <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.  
  
3. Nejdřív zkontrolujte, zda `obj` parametr je `null`a pokud ano, vrátí `false`.  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4. Další volání <xref:System.Object.ReferenceEquals%2A> a předejte mu `this` a `obj` jako parametry. Vrátí-li `true`a pak se vrátit `true`.  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5. Další pokus o přiřazení `obj` na místní proměnnou typu třídy. Když se to nepovede, odkaz je `null`. V takových případech vrátí `false`.  
  
6. Proveďte vlastní porovnání nezbytné správně porovnat aktuální deklarace identity do zadané deklarací.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje porovnání vlastní deklarace identity, kde deklarace identity prostředku je jiného než primitivního typu.  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a>Viz také:

- [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Postupy: Vytvoření vlastní deklarace](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
