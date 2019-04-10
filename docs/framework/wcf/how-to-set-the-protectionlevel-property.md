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
ms.openlocfilehash: 77596d682af6f2579ca512b0a6de1694452e025b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317776"
---
# <a name="how-to-set-the-protectionlevel-property"></a>Postupy: Nastavení vlastnosti ProtectionLevel
Použitím odpovídajícího atributu a nastavení vlastnosti můžete nastavit úroveň ochrany. Ochranu můžete nastavit na úrovni služby ovlivní všechny části všechny zprávy nebo ochrany čím dál podrobné úrovni, můžete nastavit od metody pro části zprávy. Další informace o `ProtectionLevel` vlastnost, naleznete v tématu [úroveň ochrany Principy](../../../docs/framework/wcf/understanding-protection-level.md).  
  
> [!NOTE]
>  Úrovně ochrany lze nastavit pouze v kódu, není v konfiguraci.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Všechny zprávy pro službu  
  
1. Vytvoření rozhraní pro službu.  
  
2. Použít <xref:System.ServiceModel.ServiceContractAttribute> atributu ve službě a nastavení <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> vlastnost <xref:System.Net.Security.ProtectionLevel.Sign>, jak je znázorněno v následujícím kódu (je výchozí úroveň <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>Podepsat všechny části zprávy pro operaci  
  
1. Vytvoření rozhraní pro službu a použití <xref:System.ServiceModel.ServiceContractAttribute> atribut rozhraní.  
  
2. Přidáte deklaraci metody rozhraní.  
  
3. Použít <xref:System.ServiceModel.OperationContractAttribute> atributu na metodu a nastavit <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> vlastnost <xref:System.Net.Security.ProtectionLevel.Sign>, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Ochrana proti zprávy  
 Výjimky, které jsou vyvolány ve službě může odeslat klientovi jako chyb SOAP. Další informace o vytvoření silně typované chyb, naleznete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) a [jak: Deklarace chyb v kontraktech služeb](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).  
  
#### <a name="to-protect-a-fault-message"></a>K ochraně zprávu o chybě  
  
1. Vytvořte typ, který představuje chybová zpráva. Následující příklad vytvoří třídu s názvem `MathFault` se dvěma poli.  
  
2. Použít <xref:System.Runtime.Serialization.DataContractAttribute> atribut na typ a <xref:System.Runtime.Serialization.DataMemberAttribute> atribut pro každé pole, které by měly být serializovány, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. V rozhraní, které vrátí chybu, použije <xref:System.ServiceModel.FaultContractAttribute> atributu v metodě, která se vrátí chyba a nastavit `detailType` parametru na typ třídy chyb.  
  
4. Také v konstruktoru, nastavte <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> vlastnost <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>Ochrana částí zprávy  
 Pomocí kontraktu zprávy můžete chránit části zprávy. Další informace o kontraktů zpráv najdete v tématu [použití kontraktů zpráv](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>K ochraně text zprávy  
  
1. Vytvořte typ, který představuje zprávu. Následující příklad vytvoří `Company` třída s atributem dvě pole, `CompanyName` a `CompanyID`.  
  
2. Použít <xref:System.ServiceModel.MessageContractAttribute> atribut třídy a nastavit <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> vlastnost <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
3. Použít <xref:System.ServiceModel.MessageHeaderAttribute> atributu na pole, které se budou vyjádřený jako záhlaví zprávy a nastavit `ProtectionLevel` vlastnost <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
4. Použít <xref:System.ServiceModel.MessageBodyMemberAttribute> některého z polí, která se budou vyjádřené jako část textu zprávy a nastavit `ProtectionLevel` vlastnost <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví `ProtectionLevel` vlastnost několik tříd atributů na různých místech ve službě.  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Následující kód ukazuje obory názvů požadovaných pro kompilaci příkladu kódu.  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [Princip úrovně ochrany](../../../docs/framework/wcf/understanding-protection-level.md)
