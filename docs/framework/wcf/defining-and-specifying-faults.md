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
ms.openlocfilehash: 10fc045cab995cca8d78e470d74ec9341e167308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176692"
---
# <a name="defining-and-specifying-faults"></a>Definice a určení chyb
Chyby SOAP přenášejí informace o chybovém stavu ze služby klientovi a v duplexním případě z klienta do služby interoperabilním způsobem. Toto téma popisuje, kdy a jak definovat vlastní obsah poruchy a určit, které operace je mohou vrátit. Další informace o tom, jak služba nebo duplexní klient může odesílat tyto chyby a jak klientnebo aplikace služby zpracovává tyto chyby, naleznete v [tématu Odesílání a přijímání chyb](sending-and-receiving-faults.md). Přehled zpracování chyb v aplikacích WCF (Windows Communication Foundation) naleznete [v tématu Určení a zpracování chyb ve smlouvách a službách](specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="overview"></a>Přehled  
 Deklarované chyby SOAP jsou <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> ty, ve kterých má operace, která určuje vlastní typ chyby SOAP. Nedeklarované chyby SOAP jsou ty, které nejsou zadány ve smlouvě pro operaci. Toto téma vám pomůže identifikovat tyto chybové stavy a vytvořit pro vaši službu kontrakt poruchy, kterou mohou klienti použít ke správnému zpracování těchto chybových stavů, když jsou upozorněni vlastními chybami SOAP. Základní úkoly jsou v pořadí:  
  
1. Definujte chybové stavy, o kterých by měl klient vaší služby vědět.  
  
2. Definujte vlastní obsah chyb SOAP pro tyto chybové stavy.  
  
3. Označte operace tak, aby konkrétní chyby SOAP, které jsou vyvolány jsou vystaveny klientům v WSDL.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>Definování chybových podmínek, o kterých by klienti měli vědět  
 Chyby SOAP jsou veřejně popsané zprávy, které nesou informace o chybě pro určitou operaci. Vzhledem k tomu, že jsou popsány spolu s dalšími zprávami operace v WSDL, klienti vědí, a proto očekávat, že zpracování těchto chyb při vyvolání operace. Ale protože WCF služby jsou zapsány ve spravovaném kódu, rozhodování o chybové podmínky ve spravovaném kódu mají být převedeny na chyby a vráceny klientovi poskytuje možnost oddělit chybové stavy a chyby ve vaší službě z formální chyby konverzace, kterou máte s klientem.  
  
 Například následující příklad kódu ukazuje operaci, která trvá dvě celá čísla a vrátí jiné celé číslo. Několik výjimek může být vyvolána zde, takže při navrhování chyby smlouvy, je nutné určit, které chybové podmínky jsou důležité pro vašeho klienta. V takovém případě by služba <xref:System.DivideByZeroException?displayProperty=nameWithType> měla zjistit výjimku.  
  
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
    <OperationContract> _
    Public Function Divide(a As Integer, b As Integer) As Integer
        If b = 0 Then Throw New DivideByZeroException("Division by zero!")
        Return a / b
    End Function
End Class
```
  
 V předchozím příkladu operace může vrátit vlastní chybu SOAP, která je specifická pro dělení nulou, vlastní chybu, která je specifická pro matematické operace, ale která obsahuje informace specifické pro dělení nulou, více chyb pro několik různých v chybových situacích nebo vůbec žádná chyba SOAP.  
  
### <a name="define-the-content-of-error-conditions"></a>Definování obsahu chybových podmínek  
 Jakmile je chybový stav identifikován jako stav, který může užitečně vrátit vlastní chybu SOAP, dalším krokem je definovat obsah této chyby a zajistit, aby struktura obsahu mohla být serializována. Příklad kódu v předchozí části ukazuje chybu `Divide` specifickou pro operaci, ale `Calculator` pokud existují jiné operace ve službě, pak jeden vlastní `Divide` chyba SOAP může informovat klienta o všech chybových stavech kalkulačky, včetně. Následující příklad kódu ukazuje vytvoření vlastní chyby SOAP , `MathFault`která může hlásit `Divide`chyby provedené pomocí všech matematických operací, včetně . Zatímco třída můžete zadat operaci `Operation` (vlastnost) a hodnotu, která `ProblemType` popisuje problém (vlastnost), třída a tyto vlastnosti musí být serializovatelné převést na klienta ve vlastní chyba SOAP. Proto <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> atributy <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> a se používají k tomu, aby typ a jeho vlastnosti serializovatelné a jako interoperabilní, jak je to možné.  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 Další informace o tom, jak zajistit serializovatelnost dat, naleznete [v tématu Určení přenosu dat ve smlouvách o poskytování služeb](./feature-details/specifying-data-transfer-in-service-contracts.md). Seznam podpory serializace, která <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> poskytuje, naleznete [v tématu Typy podporované serializátorem kontraktů dat](./feature-details/types-supported-by-the-data-contract-serializer.md).  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Označit operace pro vytvoření kontraktu poruchy  
 Jakmile serializovatelné datové struktury, která je vrácena jako součást vlastní chyba SOAP je definována, posledním krokem je označit smlouvu operace jako vyvolání chyby SOAP tohoto typu. Chcete-li to <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> provést, použijte atribut a předat typ vlastního datového typu, který jste vytvořili. Následující příklad kódu ukazuje, <xref:System.ServiceModel.FaultContractAttribute> jak použít atribut `Divide` k určení, že `MathFault`operace může vrátit chybu SOAP typu . Jiné operace založené na matematice nyní mohou `MathFault`také určit, že mohou vrátit .  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Operace může určit, že vrátí více než jednu vlastní <xref:System.ServiceModel.FaultContractAttribute> chybu označením této operace s více než jeden atribut.  
  
 Další krok k implementaci kontraktu poruchy v implementaci operace je popsán v tématu [Odesílání a přijímání chyb](sending-and-receiving-faults.md).  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>DŮLEŽITÉ INFORMACE O TECHNOLOGII SOAP, WSDL a interoperabilitě  
 V některých případech, zejména při spolupráci s jinými platformami, může být důležité řídit způsob, jakým se zobrazí chyba ve zprávě SOAP nebo způsob, jakým je popsána v metadatech WSDL.  
  
 Atribut <xref:System.ServiceModel.FaultContractAttribute> má <xref:System.ServiceModel.FaultContractAttribute.Name%2A> vlastnost, která umožňuje řízení wsdl název prvku poruchy, který je generován v metadatech pro tuto chybu.  
  
 Podle standardu SOAP může mít `Action`chyba `Code`, a `Reason`. Objekt `Action` je řízen <xref:System.ServiceModel.FaultContractAttribute.Action%2A> ubytovacím zařízení. Vlastnost <xref:System.ServiceModel.FaultException.Code%2A> a <xref:System.ServiceModel.FaultException.Reason%2A> vlastnost jsou obě <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> vlastnosti třídy, což <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>je nadřazená třída obecné . Vlastnost `Code` obsahuje <xref:System.ServiceModel.FaultCode.SubCode%2A> člena.  
  
 Při přístupu k neslužbám, které generují chyby, existují určitá omezení. WCF podporuje pouze chyby s typy podrobností, které popisuje schéma a které jsou kompatibilní s kontrakty dat. Například, jak je uvedeno výše, WCF nepodporuje chyby, které používají atributy XML v jejich typy podrobností nebo chyby s více než jeden prvek nejvyšší úrovně v části podrobností.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Určování a zpracování chyb v kontraktech a službách](specifying-and-handling-faults-in-contracts-and-services.md)
- [Chyby při odesílání a příjmu](sending-and-receiving-faults.md)
- [Postupy: Deklarace chyb v kontraktech služeb](how-to-declare-faults-in-service-contracts.md)
- [Princip úrovně ochrany](understanding-protection-level.md)
- [Postupy: Nastavení vlastnosti ProtectionLevel](how-to-set-the-protectionlevel-property.md)
- [Určování přenosu dat v kontraktech služby](./feature-details/specifying-data-transfer-in-service-contracts.md)
