---
title: 'Postupy: Vytvoření vlastní deklarace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: d2d170679b09eb33bea3569e1e6db8954bde3659
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622283"
---
# <a name="how-to-create-a-custom-claim"></a>Postupy: Vytvoření vlastní deklarace
Infrastruktura modelu Identity ve Windows Communication Foundation (WCF) poskytuje sadu předdefinovaných deklarací typů a práva s pomocné funkce pro vytváření <xref:System.IdentityModel.Claims.Claim> instance s těmito typy a přístupových práv. Tyto předdefinované deklarace jsou navrženy pro informace o modelu, které jsou součástí typy přihlašovacích údajů klienta, které podporuje WCF, ve výchozím nastavení. V mnoha případech jsou dostatečné; integrované deklarací identity Některé aplikace ale můžou vyžadovat vlastní deklarace identity. Deklarace identity se skládá z typ deklarace identity, prostředek, pro kterou platí deklarace identity pro a práv, která jsou s potvrzením přes tento prostředek. Toto téma popisuje, jak vytvořit vlastní deklarace identity.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>K vytvoření vlastní deklarace identity, která je založena na primitivní datový typ  
  
1.  Vytvoření vlastních deklarací identity pomocí typu deklarace identity, hodnota prostředku a právo <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktoru.  
  
    1.  Při rozhodování o jedinečnou hodnotu pro typ deklarace identity.  
  
         Typ deklarace identity je identifikátor jedinečný řetězec. Je Návrhář vlastních deklarací identity povinností ujistit se, že je jedinečný identifikátor řetězce, který se používá pro typ deklarace identity. Seznam typů deklarací identity, které jsou definovány službou WCF najdete v tématu <xref:System.IdentityModel.Claims.ClaimTypes> třídy.  
  
    2.  Zvolte primitivní datový typ a hodnotu pro prostředek.  
  
         Prostředek je objekt. Typ CLR prostředku může být jednoduchého typu, například <xref:System.String> nebo <xref:System.Int32>, nebo libovolný typ serializovat. Typ CLR prostředku musí být serializovatelný, protože deklarace identity serializují v různých fázích WCF. Primitivní typy jsou serializovatelné.  
  
    3.  Zvolte práva, která je definována WCF nebo jedinečnou hodnotu pro vlastní práva.  
  
         Práva je identifikátor jedinečný řetězec. Práva, které jsou definovány službou WCF, které jsou definovány v <xref:System.IdentityModel.Claims.Rights> třídy.  
  
         Je Návrhář vlastních deklarací identity povinností ujistit se, že je jedinečný identifikátor řetězce, který slouží k pravé straně.  
  
         Následující příklad kódu vytvoří vlastní deklarace identity s typem deklarace identity `http://example.org/claims/simplecustomclaim`, pro prostředek s názvem `Driver's License`a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> vpravo.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>K vytvoření vlastní deklarace identity, který je založen na data jiného než primitivního typu  
  
1.  Vytvoření vlastních deklarací identity pomocí typu deklarace identity, hodnota prostředku a právo <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktoru.  
  
    1.  Při rozhodování o jedinečnou hodnotu pro typ deklarace identity.  
  
         Typ deklarace identity je identifikátor jedinečný řetězec. Je Návrhář vlastních deklarací identity povinností ujistit se, že je jedinečný identifikátor řetězce, který se používá pro typ deklarace identity. Seznam typů deklarací identity, které jsou definovány službou WCF najdete v tématu <xref:System.IdentityModel.Claims.ClaimTypes> třídy.  
  
    2.  Vyberte nebo vytvořte serializovatelný jiného než primitivního typu prostředku.  
  
         Prostředek je objekt. Typ CLR prostředku musí být serializovatelný, protože deklarace identity serializují v různých fázích WCF. Primitivní typy jsou již serializovatelné.  
  
         Když je nový typ definován, použije <xref:System.Runtime.Serialization.DataContractAttribute> do třídy. Platí také <xref:System.Runtime.Serialization.DataMemberAttribute> všem členům, které potřebujete k serializaci jako součást deklarace nového typu atributu.  
  
         Následující příklad kódu definuje vlastní typ prostředku s názvem `MyResourceType`.  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  Zvolte práva, která je definována WCF nebo jedinečnou hodnotu pro vlastní práva.  
  
         Práva je identifikátor jedinečný řetězec. Práva, které jsou definovány službou WCF, které jsou definovány v <xref:System.IdentityModel.Claims.Rights> třídy.  
  
         Je Návrhář vlastních deklarací identity povinností ujistit se, že je jedinečný identifikátor řetězce, který slouží k pravé straně.  
  
         Následující příklad kódu vytvoří vlastní deklarace identity s typem deklarace identity `http://example.org/claims/complexcustomclaim`, vlastní prostředek typu `MyResourceType`a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> vpravo.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit vlastní deklarace identity s typem primitivní prostředku a vlastní deklarace identity s typem neprimitivní prostředku.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
