---
title: 'Postupy: Vytvoření vlastní deklarace identity'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: e78f577e0fd3473575fab998e55616936212ebb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185607"
---
# <a name="how-to-create-a-custom-claim"></a>Postupy: Vytvoření vlastní deklarace identity
Infrastruktura modelu identity v nadaci WCF (Windows Communication Foundation) poskytuje sadu předdefinovaných <xref:System.IdentityModel.Claims.Claim> typů deklarací identit a práv s pomocnými funkcemi pro vytváření instancí s těmito typy a právy. Tyto předdefinované deklarace identity jsou navrženy tak, aby model informace nalezené v typech pověření klienta, které wcf podporuje ve výchozím nastavení. V mnoha případech jsou vestavěné nároky dostatečné; Některé aplikace však mohou vyžadovat vlastní deklarace identity. Deklarace se skládá z typu deklarace, zdroje, pro který se deklarace vztahuje, a práva, které je uplatněno nad tímto zdrojem. Toto téma popisuje, jak vytvořit vlastní deklaraci.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>Vytvoření vlastní deklarace, která je založena na primitivním datovém typu  
  
1. Vytvořte vlastní deklaraci předáním typu deklarace, <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> hodnoty prostředku a práva konstruktoru.  
  
    1. Rozhodněte o jedinečné hodnotě pro typ deklarace.  
  
         Typ deklarace identity je jedinečný identifikátor řetězce. Je vlastní deklarace návrháře odpovědnost zajistit, že identifikátor řetězce, který se používá pro typ deklarace identity je jedinečný. Seznam typů deklarací, které jsou definovány <xref:System.IdentityModel.Claims.ClaimTypes> WCF, naleznete v části třída.  
  
    2. Zvolte primitivní datový typ a hodnotu prostředku.  
  
         Prostředek je objekt. Typ CLR prostředku může být primitivní, <xref:System.String> například nebo <xref:System.Int32>, nebo jakýkoli serializovatelný typ. Clr typ prostředku musí být serializovatelný, protože deklarace jsou serializovány na různých místech WCF. Primitivní typy jsou serializovatelné.  
  
    3. Vyberte právo, které je definováno WCF nebo jedinečnou hodnotu pro vlastní právo.  
  
         Pravé je jedinečný identifikátor řetězce. Práva, které jsou definovány WCF <xref:System.IdentityModel.Claims.Rights> jsou definovány ve třídě.  
  
         Je vlastní deklarace návrháře odpovědnost zajistit, že identifikátor řetězce, který se používá pro právo je jedinečný.  
  
         Následující příklad kódu vytvoří vlastní deklaraci `http://example.org/claims/simplecustomclaim`s typem `Driver's License`deklarace , <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> pro prostředek s názvem a s právem.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>Vytvoření vlastní deklarace, která je založena na neprimitivním datovém typu  
  
1. Vytvořte vlastní deklaraci předáním typu deklarace, <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> hodnoty prostředku a práva konstruktoru.  
  
    1. Rozhodněte o jedinečné hodnotě pro typ deklarace.  
  
         Typ deklarace identity je jedinečný identifikátor řetězce. Je vlastní deklarace návrháře odpovědnost zajistit, že identifikátor řetězce, který se používá pro typ deklarace identity je jedinečný. Seznam typů deklarací, které jsou definovány <xref:System.IdentityModel.Claims.ClaimTypes> WCF, naleznete v části třída.  
  
    2. Zvolte nebo definujte serializovatelný neprimitivní typ pro prostředek.  
  
         Prostředek je objekt. Clr typ prostředku musí být serializovatelný, protože deklarace jsou serializovány na různých místech WCF. Primitivní typy jsou již serializovatelné.  
  
         Když je definován nový typ, použijte <xref:System.Runtime.Serialization.DataContractAttribute> pro třídu. Také použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut pro všechny členy nového typu, které je třeba serializovat jako součást deklarace.  
  
         Následující příklad kódu definuje vlastní typ `MyResourceType`prostředku s názvem .  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. Vyberte právo, které je definováno WCF nebo jedinečnou hodnotu pro vlastní právo.  
  
         Pravé je jedinečný identifikátor řetězce. Práva, které jsou definovány WCF <xref:System.IdentityModel.Claims.Rights> jsou definovány ve třídě.  
  
         Je vlastní deklarace návrháře odpovědnost zajistit, že identifikátor řetězce, který se používá pro právo je jedinečný.  
  
         Následující příklad kódu vytvoří vlastní deklaraci `http://example.org/claims/complexcustomclaim`s typem deklarace , vlastní typ prostředku `MyResourceType`a s právem. <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit vlastní deklaraci s primitivním typem prostředku a vlastní deklarací s neprimitivním typem prostředku.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Správa deklarací a autorizace s modelem identity](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
