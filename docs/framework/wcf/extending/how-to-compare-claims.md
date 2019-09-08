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
ms.openlocfilehash: 29254bd661e72b926b21695ccb646480c53b5475
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797098"
---
# <a name="how-to-compare-claims"></a>Postupy: Porovnání deklarací

K provedení kontroly autorizace se používá infrastruktura modelu identity v Windows Communication Foundation (WCF). Běžným úkolem je například porovnat deklarace identity v kontextu autorizace s deklaracemi, které jsou potřeba k provedení požadované akce, nebo získat přístup k požadovanému prostředku. Toto téma popisuje, jak porovnat deklarace identity, včetně předdefinovaných a vlastních typů deklarací identity. Další informace o infrastruktuře modelu identity najdete v tématu [Správa deklarací identity a autorizace pomocí modelu identity](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).

Porovnání deklarací identity zahrnuje porovnání tří částí deklarace identity (typu, práva a prostředku) se stejnými částmi v jiné deklaraci identity, aby bylo možné zjistit, zda jsou stejné. Podívejte se na téma v následujícím příkladu.

[!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
[!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]

Obě deklarace mají typ <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>deklarace, napravo od <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>a prostředek řetězce "někdo". Jelikož jsou všechny tři části deklarace identity stejné, samotné deklarace identity jsou stejné.

Předdefinované typy deklarací se porovnávají pomocí <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody. V případě potřeby se používá kód porovnání specifický pro deklaraci identity. Například s ohledem na následující dvě deklarace hlavního názvu uživatele (UPN):

[!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
[!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]

kód porovnání v <xref:System.IdentityModel.Claims.Claim.Equals%2A> metodě vrátí `true`za předpokladu `example\someone` , že identifikuje stejného uživatele domény jakosomeone@example.com"".

Vlastní typy deklarací lze také porovnat pomocí <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody. V případech, kdy typ <xref:System.IdentityModel.Claims.Claim.Resource%2A> vrácený vlastností deklarace je jiný než primitivní typ <xref:System.IdentityModel.Claims.Claim.Equals%2A> , vrátí funkce `true` pouze v případě, že hodnoty vracené `Resource` vlastnostmi se rovnají podle <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda. V případech, kdy to není vhodné, vlastní typ vrácený `Resource` vlastností by měl <xref:System.IdentityModel.Claims.Claim.Equals%2A> přepsat metody a <xref:System.Object.GetHashCode%2A> , aby bylo možné provést jakékoli vlastní zpracování.

## <a name="comparing-built-in-claims"></a>Porovnání předdefinovaných deklarací identity

1. V případě, že jsou <xref:System.IdentityModel.Claims.Claim> zadány dvě instance <xref:System.IdentityModel.Claims.Claim.Equals%2A> třídy, použijte k provedení porovnání, jak je znázorněno v následujícím kódu.

     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]

### <a name="comparing-custom-claims-with-primitive-resource-types"></a>Porovnání vlastních deklarací s primitivními typy prostředků

1. Pro vlastní deklarace identity s primitivními typy prostředků je možné porovnání provést jako pro předdefinované deklarace, jak je znázorněno v následujícím kódu.

     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]

2. Pro vlastní deklarace identity s typy prostředků na základě struktury nebo třídy by měl typ prostředku přepsat <xref:System.IdentityModel.Claims.Claim.Equals%2A> metodu.

3. Nejprve ověřte, zda `obj` je `null`parametr, a pokud ano, vraťte `false`.

     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]

4. Další volání <xref:System.Object.ReferenceEquals%2A> a předejte `obj` `this` a jako parametry. Pokud se vrátí `true`, `true`vrátí.

     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]

5. Při dalším pokusu `obj` o přiřazení k místní proměnné typu třídy. Pokud se to nepovede, odkaz `null`je. V takových případech vrátí `false`.

6. Proveďte vlastní porovnání potřebné ke správnému porovnání aktuální deklarace identity s poskytnutou deklarací identity.

## <a name="example"></a>Příklad

Následující příklad ukazuje porovnání vlastních deklarací identity, u kterých je prostředek deklarace identity neprimitivního typu.

[!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
[!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]

## <a name="see-also"></a>Viz také:

- [Správa deklarací identity a autorizace pomocí modelu identit](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Postupy: Vytvoření vlastní deklarace identity](how-to-create-a-custom-claim.md)
