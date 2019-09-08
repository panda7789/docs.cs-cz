---
title: 'Postupy: Vytvoření vlastní deklarace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 399aba1a6ad70ae37355f529a291ab2f604af03f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797085"
---
# <a name="how-to-create-a-custom-claim"></a>Postupy: Vytvoření vlastní deklarace
Infrastruktura modelu identity ve službě Windows Communication Foundation (WCF) poskytuje sadu předdefinovaných typů deklarací identity a oprávnění s podpůrnými funkcemi pro vytváření <xref:System.IdentityModel.Claims.Claim> instancí s těmito typy a právy. Tyto předdefinované deklarace identity jsou navržené tak, aby byly v typech přihlašovacích údajů klienta, které služba WCF podporuje ve výchozím nastavení, modelované. V mnoha případech jsou předdefinované deklarace identity dostačující; Některé aplikace ale můžou vyžadovat vlastní deklarace identity. Deklarace identity se skládá z typu deklarace identity, prostředku, pro který se deklarace identity vztahuje, a práva, které je na tento prostředek uplatněno. Toto téma popisuje, jak vytvořit vlastní deklaraci identity.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>Vytvoření vlastní deklarace identity, která je založena na primitivním datovém typu  
  
1. Vytvořte vlastní deklaraci identity předáním typu deklarace identity, hodnoty prostředku a práva <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktoru.  
  
    1. Určete jedinečnou hodnotu pro typ deklarace identity.  
  
         Typ deklarace identity je jedinečný identifikátor řetězce. Je zodpovědností vlastního návrháře deklarací identity, aby se zajistilo, že identifikátor řetězce, který se používá pro typ deklarace identity, je jedinečný. Seznam typů deklarací, které jsou definovány službou WCF, naleznete v tématu <xref:System.IdentityModel.Claims.ClaimTypes> třída.  
  
    2. Vyberte primitivní datový typ a hodnotu pro daný prostředek.  
  
         Prostředek je objekt. Typ CLR prostředku může být primitivní, například <xref:System.String> nebo <xref:System.Int32>, nebo jakýkoli serializovatelný typ. Typ CLR prostředku musí být serializovatelný, protože deklarace identity jsou v různých bodech serializovány službou WCF. Primitivní typy jsou serializovatelné.  
  
    3. Vyberte právo definované službou WCF nebo jedinečnou hodnotou pro vlastní právo.  
  
         Právo je jedinečný identifikátor řetězce. Práva, která jsou definována v rámci <xref:System.IdentityModel.Claims.Rights> služby WCF, jsou definována ve třídě.  
  
         Je zodpovědností vlastního návrháře deklarací identity, aby se zajistilo, že identifikátor řetězce, který se používá pro právo, je jedinečný.  
  
         Následující příklad kódu vytvoří vlastní deklaraci identity s typem `http://example.org/claims/simplecustomclaim`deklarace identity pro prostředek s názvem `Driver's License`a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> napravo.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>Vytvoření vlastní deklarace identity, která je založena na neprimitivním datovém typu  
  
1. Vytvořte vlastní deklaraci identity předáním typu deklarace identity, hodnoty prostředku a práva <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktoru.  
  
    1. Určete jedinečnou hodnotu pro typ deklarace identity.  
  
         Typ deklarace identity je jedinečný identifikátor řetězce. Je zodpovědností vlastního návrháře deklarací identity, aby se zajistilo, že identifikátor řetězce, který se používá pro typ deklarace identity, je jedinečný. Seznam typů deklarací, které jsou definovány službou WCF, naleznete v tématu <xref:System.IdentityModel.Claims.ClaimTypes> třída.  
  
    2. Vyberte nebo definujte serializovatelný neprimitivní typ prostředku.  
  
         Prostředek je objekt. Typ CLR prostředku musí být serializovatelný, protože deklarace identity jsou v různých bodech serializovány službou WCF. Primitivní typy jsou již serializovatelné.  
  
         Pokud je definován nový typ, použijte <xref:System.Runtime.Serialization.DataContractAttribute> pro třídu. Také použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut na všechny členy nového typu, které je třeba serializovat jako součást deklarace.  
  
         Následující příklad kódu definuje vlastní typ prostředku s názvem `MyResourceType`.  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3. Vyberte právo definované službou WCF nebo jedinečnou hodnotou pro vlastní právo.  
  
         Právo je jedinečný identifikátor řetězce. Práva, která jsou definována v rámci <xref:System.IdentityModel.Claims.Rights> služby WCF, jsou definována ve třídě.  
  
         Je zodpovědností vlastního návrháře deklarací identity, aby se zajistilo, že identifikátor řetězce, který se používá pro právo, je jedinečný.  
  
         Následující příklad kódu vytvoří vlastní deklaraci identity s typem `http://example.org/claims/complexcustomclaim`deklarace identity, vlastním `MyResourceType`typem prostředku a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> napravo.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit vlastní deklaraci identity s primitivním typem prostředku a vlastní deklarací s neprimitivním typem prostředku.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Správa deklarací identity a autorizace pomocí modelu identit](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
