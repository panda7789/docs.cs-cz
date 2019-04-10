---
title: Definice a určení chyb
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], specifying
- handling faults [WCF], defining
ms.assetid: c00c84f1-962d-46a7-b07f-ebc4f80fbfc1
ms.openlocfilehash: 24c05bf41152fba2f54636cd0c15dde6fa71aa2b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299322"
---
# <a name="defining-and-specifying-faults"></a>Definice a určení chyb
Chyb SOAP předání chybová podmínka informací ze služby do klienta a v případě duplexní z klienta ke službě interoperabilní způsobem. Toto téma popisuje, kdy a jak definovat vlastní chyby obsah a určit, které operace vrátit. Další informace o jak služby nebo duplexní klient může odesílat tyto chyby a způsob, jakým aplikace klienta nebo služby zpracovává tyto chyby najdete v tématu [odesílání a příjem chyb](../../../docs/framework/wcf/sending-and-receiving-faults.md). Přehled v aplikacích Windows Communication Foundation (WCF) pro zpracování chyb, naleznete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="overview"></a>Přehled  
 Deklarovat chyb SOAP jsou ty, ve kterých se má operace <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> , která určuje vlastního typu chybu protokolu SOAP. Nedeklarovaný chyb SOAP jsou ty, které nejsou uvedené ve smlouvě operace. Toto téma vám pomůže identifikovat tyto chybové stavy a vytvoření kontraktu selhání vaší služby, který můžou klienti použít k správně zpracovat tyto chybové stavy při upozorněni prostřednictvím vlastních chyb SOAP. Základní úlohy jsou v pořadí:  
  
1. Definujte chybové stavy, které byste se měli seznámit klienta služby.  
  
2. Definujte vlastní obsah chyb SOAP pro tyto chybové podmínky.  
  
3. Označte své operace tak, aby konkrétní chyb SOAP, které generují výjimku jsou zveřejněné klientům v jazyce WSDL.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>Definování chybové stavy, které byste se měli seznámit klientů  
 Chyby protokolu SOAP se veřejně popisuje zprávy, které nesou informaci o selhání pro určitou operaci. Protože tyto toky jsou popsané společně s další operace zprávy v jazyce WSDL, klienti vědět a proto očekávat zpracovávat takové chyby při vyvolání operace. Ale protože služby WCF je zapsána ve spravovaném kódu rozhodování o tom, které chybové podmínky ve spravovaném kódu se převedou na chyby a vrátí klientovi nabízí možnost oddělení chybové stavy a chyby ve své službě od formální chyba konverzace, které máte s klientem.  
  
 Například následující příklad kódu ukazuje operaci, která přebírá dvou celých čísel a vrátí jinou celé číslo. Několik výjimky mohou být vyvolány, proto při navrhování kontrakt chyby, je třeba určit, které chybové stavy jsou důležité pro vašeho klienta. V tomto případě by měl zjistit službu <xref:System.DivideByZeroException?displayProperty=nameWithType> výjimky.  
  
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
  
 V předchozím příkladu operaci můžete buď vrátit vlastní nastala chyba protokolu SOAP, která je specifická pro dělení nulou, vlastní chyby, která je specifická pro matematických operací, ale, který obsahuje konkrétní informace o dělení hodnotou nula, více chyb pro několik různých chybové situace, nebo vůbec žádné nastala chyba protokolu SOAP.  
  
### <a name="define-the-content-of-error-conditions"></a>Definovat obsah chybové podmínky  
 Po jako ten, který se může úspěšně vrátit vlastní chybu protokolu SOAP byla zjištěna chybová podmínka, dalším krokem je definování obsah této chyby a ujistěte se, že struktura obsahu lze serializovat. Příklad kódu v předchozím oddílu ukazuje chybu, specifické pro `Divide` operaci, ale pokud se na další operace `Calculator` služby, potom jeden vlastní chybu protokolu SOAP může informovat klienta o všechny chybové stavy Kalkulačka `Divide`zahrnuté. Následující příklad kódu ukazuje vytvoření objektu vlastní nastala chyba protokolu SOAP, `MathFault`, které můžete ohlásit chyby, které bylo vytvořeno s použitím všechny matematické operace, včetně `Divide`. Zatímco třídy můžete určit operace ( `Operation` vlastnost) a hodnotu, která popisuje problém ( `ProblemType` vlastnost), třídy a tyto vlastnosti musejí být serializovatelná přenést na klienty v vlastní chybu protokolu SOAP. Proto <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> a <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> atributy se používají k výběru typu a jeho vlastnosti serializovatelné a interoperabilní co nejvíc.  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 Další informace o jak ověřit data je serializovatelný, naleznete v tématu [zadání přenosu dat v kontraktech služeb](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Seznam serializace podpora <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> poskytuje, naleznete v tématu [typy podporované serializátorem kontraktu dat](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Označit operace k navázání kontrakt chyby  
 Jakmile serializovatelný datová struktura, která je vrácena jako součást vlastní chybu protokolu SOAP je definován, posledním krokem je označit vaše smlouva operace jako vyvolává chybu protokolu SOAP daného typu. Chcete-li to provést, použijte <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> atribut a předat typ, který jste vytvořili vlastní datového typu. Následující příklad kódu ukazuje, jak používat <xref:System.ServiceModel.FaultContractAttribute> atribut určíte, že `Divide` operace může vrátit chybu protokolu SOAP typu `MathFault`. Další operace na základě matematické teď můžete také zadat, že může vrátit `MathFault`.  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Operace můžete určit, že vrátí víc vlastních chyb označením operace s více než jednou <xref:System.ServiceModel.FaultContractAttribute> atribut.  
  
 Dalším krokem, implementace kontraktu chybu v implementaci operace, je popsaný v tématu [odesílání a příjem chyb](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>Protokol SOAP, WSDL a aspekty Interoperability  
 V některých případech zejména při vzájemné spolupráci s jinými platformami, může být důležité pro řízení způsobu, jakým se zobrazí chyba ve zprávě SOAP nebo tak, jak je popsáno v metadatech WSDL.  
  
 <xref:System.ServiceModel.FaultContractAttribute> Atribut má <xref:System.ServiceModel.FaultContractAttribute.Name%2A> vlastnost, která umožňuje kontrolu nad název elementu selhání WSDL, který je vygenerován v metadatech pro tuto chybu.  
  
 Podle standardu protokolu SOAP, můžete mít chybu `Action`, `Code`a `Reason`. `Action` Řídí <xref:System.ServiceModel.FaultContractAttribute.Action%2A> vlastnost. <xref:System.ServiceModel.FaultException.Code%2A> Vlastnost a <xref:System.ServiceModel.FaultException.Reason%2A> vlastnosti jsou obě vlastnosti <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> třídu, která je nadřazená třída Obecné <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>. `Code` Obsahuje vlastnost <xref:System.ServiceModel.FaultCode.SubCode%2A> člena.  
  
 Při přístupu k jiné služby, které generují chyby, existují určitá omezení. WCF podporuje pouze chyby s typy podrobností, která popisuje schéma a, které jsou kompatibilní s kontrakty dat. Například jak je uvedeno výše, WCF nepodporuje chyb, použijte atributy XML v jejich podrobných typy nebo chyb s více než jeden element nejvyšší úrovně v sekci podrobností.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Určování a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Chyby odesílání a přijímání](../../../docs/framework/wcf/sending-and-receiving-faults.md)
- [Postupy: Deklarace chyb v kontraktech služeb](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)
- [Princip úrovně ochrany](../../../docs/framework/wcf/understanding-protection-level.md)
- [Postupy: Nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)
- [Určování přenosu dat v kontraktech služby](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
