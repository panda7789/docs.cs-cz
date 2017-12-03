---
title: "Definice a určení chyb"
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
- handling faults [WCF], specifying
- handling faults [WCF], defining
ms.assetid: c00c84f1-962d-46a7-b07f-ebc4f80fbfc1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 754c938242035549b9deb94a2fe3b975b1384fc0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="defining-and-specifying-faults"></a>Definice a určení chyb
Chyb SOAP nesou podmínku informace o chybě ze služby pro klienta a v případě duplexní z klienta ke službě umožňuje vzájemnou spolupráci způsobem. Toto téma popisuje, kdy a jak definovat vlastní chyby obsahu a určit, které operace vrátit. [!INCLUDE[crabout](../../../includes/crabout-md.md)]jak služba nebo duplexní klienta, může poslat tyto chyby a jak klienta služby nebo aplikace zpracovává těchto chyb, najdete v části [odesílání a přijímání chyb](../../../docs/framework/wcf/sending-and-receiving-faults.md). Přehled zpracování chyb v [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikace, najdete v části [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="overview"></a>Přehled  
 Deklarovaný chyb SOAP jsou ty, ve kterých se operace <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> určující vlastního typu chybu protokolu SOAP. Nedeklarovaný chyb SOAP jsou ty, které nejsou uvedené ve smlouvě operace. Toto téma vám pomůže identifikovat tyto chybové stavy a vytvoření kontraktu selhání služby, který můžou klienti používat správně zpracovat tyto chybové stavy při upozornění podle vlastních chyb SOAP. Základní úlohy jsou v pořadí:  
  
1.  Definujte podmínky chyby, které byste se měli seznámit klienta služby.  
  
2.  Definujte vlastní obsah chyb SOAP pro tyto chybové podmínky.  
  
3.  Vaše operace označte tak, aby konkrétní SOAP chyb, které vyvolají jsou viditelné na klienty v jazyce WSDL.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>Definování chybové stavy, které byste se měli seznámit klientů  
 Chyb SOAP jsou veřejně popsané zprávy, které přenosu informací o selhání určité operace. Vzhledem k tomu, že jsou popsány společně s další operace zprávy WSDL, klienti vědět a proto očekávat zpracovat takové chyby při vyvolání operace. Ale protože [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby jsou zapsané ve spravovaném kódu, při rozhodování o tom, která chyba se podmínky ve spravovaném kódu se převedou na chyb a vrátí klientovi nabízí možnost oddělit chybové stavy a chyby ve službě z formální chyba konverzace, které máte s klientem.  
  
 Například následující příklad kódu ukazuje operace, která přebírá dvě celá čísla a vrátí jiné číslo. Několik výjimek může být vyvolána tady, proto při navrhování chyba – kontrakt, je třeba určit, které chybové stavy jsou důležité pro vašeho klienta. V tomto případě by měl zjistit službu <xref:System.DivideByZeroException?displayProperty=nameWithType> výjimka.  
  
```csharp  
[ServiceContract]  
public class CalculatorService  
{  
    [OperationContract]   
    int Divide(int a, int b)  
    {  
      if (b==0) throw new Exception("Division by zero!");  
      return a/b;  
    }  
}  
```  
  
```vb  
<ServiceContract> _  
Public Class CalculatorService  
    <OperationContract]> _  
    Public Function Divide(ByVal a As Integer, ByVal b As Integer) _  
       As Integer  
      If (b==0) Then   
            Throw New Exception("Division by zero!")  
      Return a/b  
    End Function  
End Class  
```  
  
 V operaci v předchozím příkladu můžete buď vrátit vlastní chybu protokolu SOAP, která je specifická pro dělení nulou, vlastní chyby, která je specifická pro matematické operace, ale který obsahuje informace specifické pro dělení nula, několik chyb pro několik různých Chyba situacích, nebo žádná chyba protokolu SOAP na všechny.  
  
### <a name="define-the-content-of-error-conditions"></a>Definujte obsah chybové stavy  
 Jakmile jako ten, který může úspěšně vrátit vlastní chybu protokolu SOAP byla zjištěna chybový stav, dalším krokem je zadat obsah této chyby a ujistěte se, zda lze serializovat strukturu obsahu. Příklad kódu v předchozí části ukazuje chybu, specifické pro `Divide` operaci, ale pokud jsou na jiné operace `Calculator` služby, potom jeden vlastní chybu protokolu SOAP může informovat klienta všechny chybové stavy kalkulačky `Divide`zahrnuty. Následující příklad kódu ukazuje vytvoření vlastní chybu protokolu SOAP, `MathFault`, které můžete zprávy o chybách, které jsou vytvořené pomocí všechny matematické operace, včetně `Divide`. Při třídy můžete zadat operace ( `Operation` vlastnosti) a hodnotu, která popisuje problém ( `ProblemType` vlastnost), třídy a tyto vlastnosti musí být serializovatelný přenos klienta do vlastní chybu protokolu SOAP. Proto <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> a <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> atributy se používají k vytvoření typu a jeho vlastnosti, serializable a jako interoperabilních nejvíce.  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]jak ověřit data je serializovatelný naleznete [zadání přenos dat v kontraktech služby](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Seznam serializaci podpory, který <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> poskytuje, najdete v části [typy nepodporuje serializátor kontraktu dat](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Operace označit k navázání chyba – kontrakt  
 Jakmile serializovatelný datová struktura, která je vrácena, jako je definována část vlastní chybu protokolu SOAP, posledním krokem je označit smlouva operace jako byla vrácena chyba protokolu SOAP daného typu. Chcete-li to provést, použijte <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> atribut a předejte typ vlastní datový typ, který jste vytvořili. Následující příklad kódu ukazuje, jak používat <xref:System.ServiceModel.FaultContractAttribute> atribut určíte, že `Divide` operace může vrátit chybu protokolu SOAP typu `MathFault`. Jiné na základě matematické operace nyní můžete také určit, že budou vracet `MathFault`.  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Operace můžete určit, že vrací více než jeden vlastní chyby označením tuto operaci s více než jeden <xref:System.ServiceModel.FaultContractAttribute> atribut.  
  
 Na další krok, abyste implementaci kontraktu chyby v operaci implementace, je popsaný v tématu [odesílání a přijímání chyb](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>SOAP, WSDL a aspekty Interoperability  
 V některých případech zejména při interoperabilitě se službou jiné platformy, může být důležité pro řízení způsobu, jakým se zobrazí chybu do protokolu SOAP zprávy nebo způsob, jak je popsáno v metadatech WSDL.  
  
 <xref:System.ServiceModel.FaultContractAttribute> Atribut má <xref:System.ServiceModel.FaultContractAttribute.Name%2A> vlastnost, která umožňuje řízení název WSDL selhání element, který se generuje ve metadata pro tuto chybu.  
  
 Podle protokolu SOAP standard, může mít chybu `Action`, `Code`a `Reason`. `Action` Řídí <xref:System.ServiceModel.FaultContractAttribute.Action%2A> vlastnost. <xref:System.ServiceModel.FaultException.Code%2A> Vlastnost a <xref:System.ServiceModel.FaultException.Reason%2A> vlastnost jsou obě vlastnosti <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> třída, která je nadřazená třída obecná <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>. `Code` Zahrnuje vlastnost <xref:System.ServiceModel.FaultCode.SubCode%2A> člen.  
  
 Při přístupu k jiné services generujících chyb, existují určitá omezení. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]podporuje pouze chyb s typy podrobností popisující schéma a které jsou kompatibilní s kontrakty dat. Například jako uvedených výše [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] nepodporuje chyb, které se používají atributy XML v jejich podrobnosti typy nebo chyb s více než jeden element nejvyšší úrovně v sekci podrobností.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Určování a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [Chyby odesílání a přijímání](../../../docs/framework/wcf/sending-and-receiving-faults.md)  
 [Postupy: deklarace chyb v kontraktech služby](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)  
 [Princip úrovně ochrany](../../../docs/framework/wcf/understanding-protection-level.md)  
 [Postupy: nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)  
 [Určování přenosu dat v kontraktech služby](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
