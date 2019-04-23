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
ms.openlocfilehash: 2d323566aa211ced9ed76302756ed5dc82c5d2c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973717"
---
# <a name="data-member-default-values"></a>Vychozí hodnoty datových členů
V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], typy mají koncept *výchozí hodnoty*. Třeba u jakéhokoliv odkazového typu, výchozí hodnota je `null`, a pro typ integer je nula. Je čas od času žádoucí chcete vynechat, nechte datový člen ze serializovaných dat. Pokud je nastavena na výchozí hodnotu. Vzhledem k tomu, že člen má výchozí hodnotu, nemusí být serializován skutečnou hodnotu; Tato akce nemá výhody výkonu.  
  
 Chcete-li vynechat člena ze serializovaných dat. Nastavte <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> atribut `false` (výchozí hodnota je `true`).  
  
> [!NOTE]
>  Měli byste nastavit <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> vlastnost `false` pokud existuje konkrétní potřeba k tomu, například interoperability nebo data velikost snížení.  
  
## <a name="example"></a>Příklad  
 Následující kód obsahuje několik členů s <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> nastavena na `false`.  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Pokud je serializována instance této třídy, výsledek je následující: `employeeName` a `employeeID` serializován. Hodnota null pro `employeeName` a nulovou hodnotu pro `employeeID` je explicitně součástí serializovaná data. Ale `position`, `salary`, a `bonus` členy nejsou serializována. Nakonec `targetSalary` serializován jako obvykle, i když <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> je nastavena na `false`, protože 57800 neodpovídá výchozí hodnotě .NET pro celé číslo, které je nula.  
  
### <a name="xml-representation"></a>Reprezentovaný pomocí XML  
 Pokud v předchozím příkladu je serializován do formátu XML, reprezentace je podobný následujícímu.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 `xsi:nil` Atribut je speciální atribut v oboru názvů instance schématu XML World Wide Web Consortium (W3C), který poskytuje interoperabilní způsob, jak explicitně reprezentaci hodnoty null. Mějte na paměti, že není žádná vůbec v souboru XML o umístění, salary a bonusové datové členy. Přijímající straně dokáže interpretovat jako `null`, nula, a `null`v uvedeném pořadí. Neexistuje žádná záruka, který deserializátor třetích stran umožňuje správnou interpretaci, což je důvod, proč tento model se nedoporučuje. <xref:System.Runtime.Serialization.DataContractSerializer> Třídy vždy vybere správnou interpretaci pro chybějící hodnoty.  
  
### <a name="interaction-with-isrequired"></a>Interakce s IsRequired  
 Jak je popsáno v [Správa verzí kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md), <xref:System.Runtime.Serialization.DataMemberAttribute> atribut má <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnosti (výchozí hodnota je `false`). Vlastnost určuje, zda daný datový člen musí být součástí serializovaná data, když je deserializován. Pokud `IsRequired` je nastavena na `true`, (což znamená, že hodnota musí být k dispozici) a <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> je nastavena na `false` (to znamená, že hodnota nesmí být k dispozici, pokud je nastavena na výchozí hodnotu), nemůže být výchozí hodnoty pro tento datový člen serializovat, protože výsledky budou odporuje. Pokud datový člen je nastavena na výchozí hodnotu (obvykle `null` nebo nula) a dojde k pokusu o serializace, <xref:System.Runtime.Serialization.SerializationException> je vyvolána výjimka.  
  
### <a name="schema-representation"></a>Reprezentace schématu  
 Podrobnosti o reprezentaci schématu XML definice jazyk (XSD) schématu datových členů při `EmitDefaultValue` je nastavena na `false` jsou popsány v [schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Toto je však stručný přehled:  
  
-   Když <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> je nastavena na `false`, je reprezentován ve schématu jako poznámky specifické pro Windows Communication Foundation (WCF). Neexistuje žádný interoperabilní způsob, jak reprezentaci těchto informací. Konkrétně není pro tento účel použít atribut "Výchozí" ve schématu `minOccurs` atribut má vliv pouze <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> nastavení a `nillable` atribut má vliv pouze typ datového členu.  
  
-   Použít skutečné výchozí hodnota není k dispozici ve schématu. Záleží přijímající koncového bodu správně interpretovat element nebyl nalezen.  
  
 Při importu schématu <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> vlastností se automaticky nastaví na `false` vždy, když se dříve zjistí poznámky specifické pro WCF uvedené. Je také nastavena na `false` pro typy odkazů, které mají `nillable` vlastnost nastavena na hodnotu `false` pro zajištění podpory scénářů konkrétní vzájemná funkční spolupráce, nejčastějších při využívání [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
