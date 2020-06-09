---
title: Vychozí hodnoty datových členů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data members [WCF], default values
- data members [WCF]
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
ms.openlocfilehash: e4eaaec880ecfcff24d9d5b4e8347a84738e070b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593475"
---
# <a name="data-member-default-values"></a>Vychozí hodnoty datových členů
V .NET Framework typy mají koncept *výchozích hodnot*. Například pro libovolný typ odkazu je výchozí hodnota `null` a pro typ integer je nula. Občas je žádoucí vynechat datový člen ze serializovaných dat, když je nastaven na jeho výchozí hodnotu. Vzhledem k tomu, že má člen výchozí hodnotu, není nutné serializovat skutečnou hodnotu; Tato výhoda má vliv na výkon.  
  
 Chcete-li vynechat člena ze serializovaných dat, nastavte <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> atributu na `false` (výchozí hodnota je `true` ).  
  
> [!NOTE]
> Vlastnost byste měli nastavit <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> na `false` , pokud je to konkrétní potřeba, například pro interoperabilitu nebo omezení velikosti dat.  
  
## <a name="example"></a>Příklad  
 Následující kód má několik členů s <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> nastavením na `false` .  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Je-li instance této třídy serializován, výsledek je následující: `employeeName` a `employeeID` je serializován. Hodnota null pro `employeeName` a nulová hodnota pro `employeeID` je explicitně součástí serializovaných dat. Nicméně `position` `salary` Členové, a nejsou `bonus` serializováni. Nakonec `targetSalary` je serializován jako obvykle, i když <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> je vlastnost nastavena na `false` , protože 57800 se neshoduje s výchozí hodnotou .NET pro celé číslo, což je nula.  
  
### <a name="xml-representation"></a>Reprezentace XML  
 Pokud je předchozí příklad serializován do XML, reprezentace je podobná následující.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 `xsi:nil`Atribut je speciální atribut v oboru názvů instance schématu XML konsorcium World Wide Web (W3C), který poskytuje interoperabilní způsob, jak explicitně reprezentovat hodnotu null. Všimněte si, že v XML nejsou žádné informace o pozicích, platech a datových členech bonusu. Konec příjmu může tyto hodnoty interpretovat jako `null` , nula a v `null` uvedeném pořadí. Není zaručeno, že deserializátor třetí strany může provést správnou interpretaci, což znamená, proč se tento model nedoporučuje. <xref:System.Runtime.Serialization.DataContractSerializer>Třída vždy vybere správnou interpretaci chybějících hodnot.  
  
### <a name="interaction-with-isrequired"></a>Interakce s-Required  
 Jak je popsáno v tématu [Správa verzí kontraktů dat](data-contract-versioning.md), <xref:System.Runtime.Serialization.DataMemberAttribute> má atribut <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost (výchozí hodnota je `false` ). Vlastnost označuje, zda musí být daný datový člen přítomen v serializovaných datech při deserializaci. Pokud `IsRequired` je nastaveno na `true` , (což znamená, že musí být přítomna hodnota) a <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> je nastavena na (to znamená `false` , že hodnota nesmí být přítomna, pokud je nastavena na výchozí hodnotu), nelze výchozí hodnoty pro tento datový člen serializovat, protože výsledky by byly protichůdny. Pokud je takový datový člen nastaven na výchozí hodnotu (obvykle `null` nebo nula) a je proveden pokus o serializaci, <xref:System.Runtime.Serialization.SerializationException> je vyvolána.  
  
### <a name="schema-representation"></a>Reprezentace schématu  
 Podrobnosti reprezentace schématu XML schématu definice jazyka (XSD), pokud `EmitDefaultValue` je vlastnost nastavena na hodnotu, je `false` popsána v tématu [referenční informace schématu kontraktu dat](data-contract-schema-reference.md). Následující je však stručný přehled:  
  
- Pokud <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> je parametr nastaven na hodnotu `false` , je reprezentován ve schématu jako anotace specifickou pro Windows Communication Foundation (WCF). Neexistuje žádný vzájemně ovladatelný způsob, jak tyto informace zastupovat. Konkrétně atribut "default" ve schématu se pro tento účel nepoužívá, `minOccurs` atribut je ovlivněn pouze <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> nastavením a `nillable` atribut je ovlivněn pouze typem datového členu.  
  
- Skutečná výchozí hodnota, která se má použít, není ve schématu přítomná. Je k dispozici koncový bod ke správnému interpretaci chybějícího prvku.  
  
 Při importu schématu <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> je vlastnost automaticky nastavena na `false` pokaždé, když je zjištěna Poznámka specifická pro WCF. Je také nastaveno na `false` pro typy odkazů, které mají `nillable` vlastnost nastavenou na `false` podporu specifických scénářů interoperability, které se běžně vyskytují při využívání webových služeb ASP.NET.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
