---
title: "Postupy: vytvoření vlastních deklarací identity"
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
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e1e85d1815d1fbde25e1963a54cce8f02f5344a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-claim"></a>Postupy: vytvoření vlastních deklarací identity
Infrastruktura Identity modelu v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] poskytuje sadu předdefinovaných typy a práva pomocných funkcí pro vytváření <xref:System.IdentityModel.Claims.Claim> instancí s těmito typy a práva. Tyto integrované deklarace jsou navrženy pro informace o modelu, které se nacházejí v klientovi přihlašovací údaje typy, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje ve výchozím nastavení. V mnoha případech jsou předdefinované deklarace identity dostatečná; Některé aplikace ale můžou vyžadovat vlastní deklarace. Deklarace identity se skládá z typ deklarace identity, prostředků, pro kterou platí deklarace identity k a práv, která jsou uplatňovaná přes tento prostředek. Toto téma popisuje postup vytvoření vlastních deklarací identity.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>K vytvoření vlastních deklarací identity, která je založená na primitivní datový typ  
  
1.  Vytvoření vlastních deklarací identity pomocí předání typu deklarace, hodnota prostředků a právo <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktor.  
  
    1.  Rozhodněte o jedinečnou hodnotu pro typ deklarace identity.  
  
         Typ deklarace identity je řetězec jedinečný identifikátor. Je zodpovědností Návrháře vlastních deklarací identity k zajištění, že je jedinečný identifikátor řetězec, který se používá pro typ deklarace identity. Seznam typů deklarací identity, které jsou definovány [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], najdete v článku <xref:System.IdentityModel.Claims.ClaimTypes> třídy.  
  
    2.  Zvolte primitivní datový typ a hodnotu pro daný prostředek.  
  
         Prostředek je objekt. Typ CLR prostředek může být primitivní, jako například <xref:System.String> nebo <xref:System.Int32>, nebo kterýkoli typ serializable. Typ CLR prostředku musí být serializovatelný, protože deklarace identity jsou v různých bodů pomocí serializovány [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Primitivní typy jsou serializable.  
  
    3.  Zvolte vpravo, která jsou definována ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nebo jedinečnou hodnotu pro vlastní práva.  
  
         Pravém je identifikátor jedinečného řetězce. Práva, které jsou definovány [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jsou definovány v <xref:System.IdentityModel.Claims.Rights> třídy.  
  
         Je odpovědností Návrháře vlastních deklarací identity zajistit, že je jedinečný identifikátor řetězec, který se používá pro vpravo.  
  
         Následující příklad kódu vytvoří vlastních deklarací identity s typem deklarace identity `http://example.org/claims/simplecustomclaim`, pro prostředek s názvem `Driver's License`a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> správné.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>K vytvoření vlastních deklarací identity, která je založená na jiný primitivní datový typ  
  
1.  Vytvoření vlastních deklarací identity pomocí předání typu deklarace, hodnota prostředků a právo <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktor.  
  
    1.  Rozhodněte o jedinečnou hodnotu pro typ deklarace identity.  
  
         Typ deklarace identity je řetězec jedinečný identifikátor. Je zodpovědností Návrháře vlastních deklarací identity k zajištění, že je jedinečný identifikátor řetězec, který se používá pro typ deklarace identity. Seznam typů deklarací identity, které jsou definovány [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], najdete v článku <xref:System.IdentityModel.Claims.ClaimTypes> třídy.  
  
    2.  Zvolte nebo definovat serializovatelný není primitivní typ prostředku.  
  
         Prostředek je objekt. Typ CLR prostředku musí být serializovatelný, protože deklarace identity jsou v různých bodů pomocí serializovány [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Primitivní typy jsou již serializable.  
  
         Pokud je nový typ definované, použít <xref:System.Runtime.Serialization.DataContractAttribute> k třídě. Platí také <xref:System.Runtime.Serialization.DataMemberAttribute> atribut všichni členové nový typ, který je potřeba serializovat v rámci deklarace identity.  
  
         Následující příklad kódu definuje vlastní typ prostředku s názvem `MyResourceType`.  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  Zvolte vpravo, která jsou definována ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nebo jedinečnou hodnotu pro vlastní práva.  
  
         Pravém je identifikátor jedinečného řetězce. Práva, které jsou definovány [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jsou definovány v <xref:System.IdentityModel.Claims.Rights> třídy.  
  
         Je odpovědností Návrháře vlastních deklarací identity zajistit, že je jedinečný identifikátor řetězec, který se používá pro vpravo.  
  
         Následující příklad kódu vytvoří vlastních deklarací identity s typem deklarace identity `http://example.org/claims/complexcustomclaim`, typ vlastní prostředek `MyResourceType`a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> správné.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit vlastní deklarace identity s typem primitivní prostředku a vlastních deklarací identity s typem prostředku není primitivní.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Správa deklarací a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Správa deklarací a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
