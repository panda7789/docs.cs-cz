---
title: 'Postupy: Nastavení vlastnosti ProtectionLevel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 50e14e1250055efcbc48597be3dcfac2e56371ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501530"
---
# <a name="how-to-set-the-protectionlevel-property"></a>Postupy: Nastavení vlastnosti ProtectionLevel
Úroveň ochrany můžete nastavit tak, že použití odpovídajícího atributu a nastavení vlastnosti. Můžete nastavit ochranu na úrovni služby a ovlivňují všechny části každé zprávy nebo můžete nastavit ochranu stále podrobné úrovni, z metody části zprávy. Další informace o `ProtectionLevel` vlastnost, najdete v části [úroveň ochrany Principy](../../../docs/framework/wcf/understanding-protection-level.md).  
  
> [!NOTE]
>  Úrovně ochrany lze nastavit pouze v kódu, není v konfiguraci.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Chcete-li odhlásit všechny zprávy pro službu  
  
1.  Vytvořte rozhraní pro službu.  
  
2.  Použít <xref:System.ServiceModel.ServiceContractAttribute> atribut služby a nastavte <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> vlastnost <xref:System.Net.Security.ProtectionLevel.Sign>, jak je znázorněno v následujícím kódu (výchozí úroveň je <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>K podepisování všech částí zprávy operace  
  
1.  Vytvoření rozhraní pro službu a použití <xref:System.ServiceModel.ServiceContractAttribute> atribut rozhraní.  
  
2.  Přidejte deklaraci metodu rozhraní.  
  
3.  Použít <xref:System.ServiceModel.OperationContractAttribute> atribut metodu a nastavit <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> vlastnost <xref:System.Net.Security.ProtectionLevel.Sign>, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Ochrana chybové zprávy  
 Výjimky, které jsou vyvolány ve službě může odeslat klientovi jako chyb SOAP. Další informace o vytváření silně typované chyb, najdete v části [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) a [postupy: deklarace chyb v kontraktech služby](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).  
  
#### <a name="to-protect-a-fault-message"></a>K ochraně zprávu o chybě  
  
1.  Vytvořte typ, který představuje zprávu chyby. Následující příklad vytvoří třídu s názvem `MathFault` se dvěma poli.  
  
2.  Použít <xref:System.Runtime.Serialization.DataContractAttribute> atribut typu a <xref:System.Runtime.Serialization.DataMemberAttribute> atribut každé pole, které by měly být serializovány, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3.  V rozhraní, které vrátí chybu, použít <xref:System.ServiceModel.FaultContractAttribute> atribut metody, která vrátí chybu a nastavit `detailType` parametr pro typ třídy selhání.  
  
4.  V konstruktoru, nastavte také <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> vlastnost <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>Ochrana částí zprávy  
 Kontrakt zprávy použijte k ochraně části zprávy. Další informace o kontrakty zpráv najdete v tématu [pomocí kontrakty zpráv](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>K ochraně text zprávy  
  
1.  Vytvořte typ, který představuje zprávu. Následující příklad vytvoří `Company` třídy se dvěma poli `CompanyName` a `CompanyID`.  
  
2.  Použít <xref:System.ServiceModel.MessageContractAttribute> atribut třídy a nastavte <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> vlastnost <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
3.  Použít <xref:System.ServiceModel.MessageHeaderAttribute> atribut pole, které bude vyjádřený jako záhlaví zprávy a nastavit `ProtectionLevel` vlastnost <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
4.  Použít <xref:System.ServiceModel.MessageBodyMemberAttribute> pro každé pole, které bude vyjádřený jako část textu zprávy a nastavit `ProtectionLevel` vlastnost <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující příklad nastavuje `ProtectionLevel` vlastnost třídy několik atributů na různých místech ve službě.  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Následující kód ukazuje obory názvů potřebné ke kompilaci ukázkový kód.  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.MessageContractAttribute>  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
 [Princip úrovně ochrany](../../../docs/framework/wcf/understanding-protection-level.md)
