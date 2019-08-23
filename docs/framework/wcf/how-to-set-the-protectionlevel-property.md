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
ms.openlocfilehash: 222fda180923cdc7b0d7b7ab413c151c69add259
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950982"
---
# <a name="how-to-set-the-protectionlevel-property"></a>Postupy: Nastavení vlastnosti ProtectionLevel
Úroveň ochrany můžete nastavit pomocí vhodného atributu a nastavením vlastnosti. Ochranu na úrovni služby můžete nastavit tak, aby ovlivnila všechny části každé zprávy, nebo můžete nastavit ochranu na stále podrobnějších úrovních, od metod až po části zpráv. Další informace o této `ProtectionLevel` vlastnosti naleznete v tématu [Principy úrovně ochrany](../../../docs/framework/wcf/understanding-protection-level.md).  
  
> [!NOTE]
> Úrovně ochrany lze nastavit pouze v kódu, nikoli v konfiguraci.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Podepsání všech zpráv pro službu  
  
1. Vytvořte rozhraní pro službu.  
  
2. Použijte atribut pro službu a <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> nastavte vlastnost na <xref:System.Net.Security.ProtectionLevel.Sign>, jak je znázorněno v následujícím kódu (výchozí úroveň je <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>). <xref:System.ServiceModel.ServiceContractAttribute>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>Podepsání všech částí zprávy pro operaci  
  
1. Vytvořte rozhraní pro službu a použijte <xref:System.ServiceModel.ServiceContractAttribute> atribut pro rozhraní.  
  
2. Přidejte do rozhraní deklaraci metody.  
  
3. Použijte atribut na metodu a <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> nastavte vlastnost na <xref:System.Net.Security.ProtectionLevel.Sign>, jak je znázorněno v následujícím kódu. <xref:System.ServiceModel.OperationContractAttribute>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Ochrana chybových zpráv  
 Výjimky, které jsou vyvolány ve službě, lze odeslat klientovi jako chyby protokolu SOAP. Další informace o vytváření chyb silného typu najdete v tématech [určení a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) a [postup: Deklarace chyb v kontraktech](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)služeb.  
  
#### <a name="to-protect-a-fault-message"></a>Ochrana zprávy o chybě  
  
1. Vytvořte typ, který představuje zprávu o chybě. Následující příklad vytvoří třídu s názvem `MathFault` se dvěma poli.  
  
2. Použijte atribut pro typ a atribut pro každé pole, které by mělo být serializován, jak je znázorněno v následujícím kódu. <xref:System.Runtime.Serialization.DataMemberAttribute> <xref:System.Runtime.Serialization.DataContractAttribute>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. V rozhraní, které vrátí chybu, použijte <xref:System.ServiceModel.FaultContractAttribute> atribut na metodu, která vrátí chybu a `detailType` nastavte parametr na typ třídy selhání.  
  
4. Také v konstruktoru nastavte <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> vlastnost na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>Ochrana částí zprávy  
 Pomocí kontraktu zprávy můžete chránit části zprávy. Další informace o kontraktech zpráv najdete v tématu [Použití kontraktů zpráv](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>Ochrana textu zprávy  
  
1. Vytvořte typ, který představuje zprávu. Následující příklad vytvoří `Company` třídu se dvěma `CompanyName` poli a `CompanyID`.  
  
2. Použijte atribut pro třídu a <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> nastavte vlastnost na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>hodnotu. <xref:System.ServiceModel.MessageContractAttribute>  
  
3. Použijte atribut na pole, které bude vyjádřeno jako záhlaví zprávy a `ProtectionLevel` nastavte vlastnost na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>hodnotu. <xref:System.ServiceModel.MessageHeaderAttribute>  
  
4. Použijte pro každé pole, které bude vyjádřeno jako součást textu zprávy, a `ProtectionLevel` nastavte vlastnost na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>hodnotu, jak je znázorněno v následujícím příkladu. <xref:System.ServiceModel.MessageBodyMemberAttribute>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví `ProtectionLevel` vlastnost několika tříd atributů na různých místech služby.  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Následující kód ukazuje obory názvů, které jsou požadovány pro zkompilování ukázkového kódu.  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [Princip úrovně ochrany](../../../docs/framework/wcf/understanding-protection-level.md)
