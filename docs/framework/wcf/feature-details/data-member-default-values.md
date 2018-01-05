---
title: "Vychozí hodnoty datových členů"
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
- data members [WCF], default values
- data members [WCF]
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33f093beb022804bbdbccf1177404e128d198dd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="data-member-default-values"></a>Vychozí hodnoty datových členů
V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], typy mají koncept *výchozí hodnoty*. Například pro libovolného typu odkaz na výchozí hodnota je `null`, a pro typ integer je nula. Je občas žádoucí vynechat data člena z serializovaná data, když je nastaveno na výchozí hodnotu. Protože člen má výchozí hodnotu, nemusí být serializovány skutečnou hodnotu; Tato akce nemá využít výkonu.  
  
 Chcete-li vynechejte člena z serializovaná data, nastavte <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> atribut `false` (výchozí hodnota je `true`).  
  
> [!NOTE]
>  Měli byste nastavit <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> vlastnost `false` Pokud je konkrétní potřebu Uděláte to tak, například konkrétní interoperabilitu nebo data velikost snížení.  
  
## <a name="example"></a>Příklad  
 Následující kód má několik členů s <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> nastavena na `false`.  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Pokud se instance této třídy je serializováno, výsledek je následující: `employeeName` a `employeeID` serializován. Hodnota null pro `employeeName` a nulovou hodnotu `employeeID` je explicitně součástí serializovaná data. Ale `position`, `salary`, a `bonus` nejsou serializované členy. Nakonec `targetSalary` serializován obvyklým způsobem, i když <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> je nastavena na `false`, protože 57800 neodpovídá .NET výchozí hodnota pro celé číslo, které je nulová.  
  
### <a name="xml-representation"></a>Reprezentovaný pomocí XML  
 Pokud předchozí příklad serializován do formátu XML, reprezentace je podobný následujícímu.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 `xsi:nil` Se o zvláštní atribut instance oboru názvů schématu XML World Wide Web Consortium (W3C), který poskytuje umožňuje vzájemnou spolupráci způsob, jak explicitně představují hodnotu null. Všimněte si, že žádné informace o všech v souboru XML o pozici, mzda a bonusové datových členů. Koncové straně příjmu můžete interpretovat jako `null`, nula, a `null`, v uvedeném pořadí. Neexistuje žádná záruka, který deserializátor třetích stran může provádět správné interpretace, proto tento vzor se nedoporučuje. <xref:System.Runtime.Serialization.DataContractSerializer> Třída vždy vybere správný interpretace pro chybějící hodnoty.  
  
### <a name="interaction-with-isrequired"></a>Interakce s IsRequired  
 Jak je popsáno v [Správa verzí kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md), <xref:System.Runtime.Serialization.DataMemberAttribute> atribut má <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnosti (výchozí hodnota je `false`). Vlastnost určuje, zda daná data člena musí být v serializovaných datech. Pokud je deserializován. Pokud `IsRequired` je nastaven na `true`, (což znamená, že hodnota musí být přítomen) a <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> je nastaven na `false` (což znamená, že hodnota nesmí být přítomen, pokud je nastaveno na výchozí hodnotu), nemůže být výchozí hodnoty pro tento datový člen serializovat, protože by byl odporuje výsledky. Pokud datový člen nastavená na výchozí hodnotu (obvykle `null` nebo nula) a je pokus serializaci, <xref:System.Runtime.Serialization.SerializationException> je vyvolána výjimka.  
  
### <a name="schema-representation"></a>Reprezentace schématu  
 Podrobnosti o definice schématu XML jazyk (XSD) schématu reprezentaci datových členů při `EmitDefaultValue` je nastavena na `false` jsou popsané v [Přehled schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Toto je však stručný přehled:  
  
-   Když <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> je nastaven na `false`, je zobrazena ve schématu jako specifické pro poznámky [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Neexistuje žádný způsob umožňuje vzájemnou spolupráci představují tyto informace. Konkrétně není pro tento účel použít atribut "Výchozí" ve schématu `minOccurs` atribut má vliv pouze <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> nastavení a `nillable` atribut má vliv pouze podle typu datový člen.  
  
-   Použít skutečné výchozí hodnota se nenachází ve schématu. Je přijímací koncový bod správně interpretovat chybí element.  
  
 Při importu schématu <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> je automaticky nastavena na `false` vždy, když [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-dříve zjištěna konkrétní poznámky uvedených. Je také nastavena na `false` pro odkazové typy, které mají `nillable` vlastnost nastavena na hodnotu `false` podporu konkrétní interoperabilita scénářů, které běžně nastat při využívání [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>
