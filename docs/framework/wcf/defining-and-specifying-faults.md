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
ms.openlocfilehash: 37ded0aad547df616d2b8b73e7cb145514da080d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972370"
---
# <a name="defining-and-specifying-faults"></a>Definice a určení chyb
Chyby protokolu SOAP vyjadřují informace chybové podmínky ze služby klientovi a v duplexovém případě od klienta až po službu. Toto téma popisuje, kdy a jak definovat vlastní obsah chyby a určit, které operace se můžou vrátit. Další informace o tom, jak může služba nebo duplexní klient odesílat tyto chyby a jak aplikace klienta nebo služby tyto chyby zpracovává, najdete v tématu [odesílání a příjem chyb](../../../docs/framework/wcf/sending-and-receiving-faults.md). Přehled zpracování chyb v aplikacích Windows Communication Foundation (WCF) najdete v tématu [určení a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="overview"></a>Přehled  
 Deklarované chyby protokolu SOAP jsou ty, ve kterých operace má a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> určuje vlastní typ chyby SOAP. Nedeklarované chyby protokolu SOAP jsou ty, které nejsou ve kontraktu pro operaci zadané. Toto téma vám pomůže identifikovat tyto chybové podmínky a vytvořit kontrakt selhání pro vaši službu, kterou klienti můžou použít k řádnému zpracování těchto chybových stavů, když jsou upozorňováni vlastními chybami protokolu SOAP. Základní úlohy jsou v uvedeném pořadí:  
  
1. Definujte chybové stavy, o které by měl klient služby informovat.  
  
2. Zadejte vlastní obsah chyb protokolu SOAP pro tyto chybové stavy.  
  
3. Označte své operace tak, aby konkrétní chyby SOAP, které vyvolávají, byly vystaveny klientům v jazyce WSDL.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>Definování chybových podmínek, o kterých mají klienti informace  
 Chyby protokolu SOAP jsou veřejně popsány zprávy, které obsahují informace o chybě konkrétní operace. Vzhledem k tomu, že jsou popsány spolu s jinými operačními zprávami v jazyce WSDL, klienti ví a, proto při vyvolání operace očekávat tyto chyby. Vzhledem k tomu, že služby WCF jsou napsány ve spravovaném kódu, rozhodování o tom, které chybové stavy ve spravovaném kódu mají být převedeny na chyby a vráceny klientovi, získáte možnost oddělit chybové podmínky a chyby ve službě od formální chyby. konverzace, kterou máte s klientem.  
  
 Například následující příklad kódu ukazuje operaci, která přijímá dvě celá čísla a vrací jiné celé číslo. V tuto chvíli může být vyvoláno několik výjimek, takže při navrhování smlouvy o selhání je třeba určit, které chybové stavy jsou pro vašeho klienta důležité. V takovém případě by služba měla detekovat <xref:System.DivideByZeroException?displayProperty=nameWithType> výjimku.  
  
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
  
 V předchozím příkladu může operace vrátit buď vlastní chybu SOAP, která je specifická pro dělení nulou, vlastní chybu, která je specifická pro matematické operace, ale obsahuje informace specifické pro dělení nulou, více chyb pro několik různých chybové situace nebo žádná chyba protokolu SOAP.  
  
### <a name="define-the-content-of-error-conditions"></a>Definování obsahu chybových podmínek  
 Jakmile je zjištěna chybová podmínka jako ta, která může užitečné vrátit vlastní chybu SOAP, je dalším krokem definování obsahu této chyby a zajištění serializace struktury obsahu. Příklad kódu v předchozí části ukazuje chybu specifickou pro `Divide` operaci, ale `Calculator` v případě, že jsou u služby jiné operace, může jedna vlastní chyba protokolu SOAP informovat klienta o všech chybových podmínkách `Divide`kalkulačky.zahrnuto. Následující příklad kódu ukazuje vytvoření vlastní chyby protokolu SOAP, `MathFault`která může hlásit chyby vytvořené pomocí všech matematických operací, včetně. `Divide` I když třída může specifikovat operaci ( `Operation` vlastnost) a hodnotu, která popisuje problém `ProblemType` (vlastnost), třída a tyto vlastnosti musí být serializovatelné, aby je bylo možné přenést do klienta ve vlastní chybě protokolu SOAP. Proto se atributy <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType>apoužívají k tomu, aby byl typ a jeho vlastnosti serializovatelný a jak je možné je vzájemně fungovat. <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 Další informace o tom, jak zajistit, aby vaše data byla serializovatelný, najdete v tématu [určení přenos dat v kontraktech služeb](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Seznam podpory serializace, která <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> poskytuje, najdete v tématu [typy podporované serializátorem kontraktu dat](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Označení operací k navázání smlouvy o selhání  
 Jakmile je definována serializovatelný datová struktura, která je vrácena jako součást vlastní chyby protokolu SOAP, je posledním krokem označení kontraktu operace jako vyvolání chyby protokolu SOAP tohoto typu. Chcete-li to provést, <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> použijte atribut a předejte typ vlastního typu dat, který jste sestavili. Následující příklad kódu ukazuje <xref:System.ServiceModel.FaultContractAttribute> `Divide` , jak použít atribut k určení toho, že operace může vracet chybu SOAP typu `MathFault`. Jiné operace založené na matematických operacích teď můžou také určit, že `MathFault`můžou vracet.  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Operace může určit, že vrátí více než jednu vlastní chybu tím, že označíte tuto operaci s více než <xref:System.ServiceModel.FaultContractAttribute> jedním atributem.  
  
 Dalším krokem je implementace kontraktu chyby v implementaci vaší operace, která je popsaná v tématu [odesílání a příjem chyb](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>Požadavky SOAP, WSDL a interoperability  
 V některých případech, zejména při spolupráci s jinými platformami, může být důležité řídit způsob, jakým se chyba objevuje ve zprávě SOAP, nebo jak je popsáno v metadatech WSDL.  
  
 <xref:System.ServiceModel.FaultContractAttribute> Atribut<xref:System.ServiceModel.FaultContractAttribute.Name%2A> má vlastnost, která umožňuje řízení názvu elementu chyby WSDL, který je generován v metadatech pro tuto chybu.  
  
 Podle standardu SOAP může chyba mít `Action` `Code`, a, a `Reason`. <xref:System.ServiceModel.FaultContractAttribute.Action%2A> Vlastnost `Action` je řízena vlastností. Vlastnost a <xref:System.ServiceModel.FaultException.Reason%2A> vlastnost<xref:System.ServiceModel.FaultException?displayProperty=nameWithType> jsou obě vlastnosti třídy, které jsou nadřazenou třídou obecného <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>. <xref:System.ServiceModel.FaultException.Code%2A> `Code` Vlastnost<xref:System.ServiceModel.FaultCode.SubCode%2A> obsahuje člena.  
  
 Při přístupu k jiným než službám, které generují chyby, existují určitá omezení. WCF podporuje pouze chyby s typy podrobností, které schéma popisuje a které jsou kompatibilní s kontrakty dat. Například jak je uvedeno výše, WCF nepodporuje chyby, které používají atributy XML v jejich typech podrobností, nebo chyby s více než jedním prvkem nejvyšší úrovně v sekci podrobností.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Určování a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Chyby při odesílání a příjmu](../../../docs/framework/wcf/sending-and-receiving-faults.md)
- [Postupy: Deklarace chyb v kontraktech služeb](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)
- [Princip úrovně ochrany](../../../docs/framework/wcf/understanding-protection-level.md)
- [Postupy: Nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)
- [Určování přenosu dat v kontraktech služby](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
