---
title: "Člen přetížení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2c84d70fb8c05dc295fc807c9a59085c47d0f455
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="member-overloading"></a>Člen přetížení
Člen přetížení znamená vytvoření dvou nebo více členů na stejný typ, který se liší pouze v číslo nebo typ parametry, ale mají stejný název. Například v následujícím příkladu `WriteLine` je přetížena metoda:  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 Protože parametry mohou obsahovat pouze metody, konstruktory a indexované vlastnosti, mohou být přetíženy pouze ty členy.  
  
 Přetížení je jedním z nejdůležitějších techniky pro zlepšení použitelnost, produktivity a čitelnost opakovaně použitelné knihovny. Přetížení pro počet parametrů je možné poskytnout jednodušší verze konstruktorů a metod. Přetížení na typ parametru umožňuje použít stejný název člena pro členy provádí na vybranou sadu různé typy stejné operace.  
  
 **PROVEĎTE ✓** zkuste použít parametr popisné názvy označíte, výchozí hodnotu použitou kratší přetíženími.  
  
 **X nepoužívejte** nahodile různými názvy parametrů v přetížení. Pokud parametr v jedním přetížením představuje stejné vstupu jako parametr v jiné přetížení, parametry musí mít stejný název.  
  
 **X nepoužívejte** nekonzistentní v pořadí parametrů v přetížen členy. Parametry se stejným názvem by se zobrazit ve stejné pozici v všechny přetížení.  
  
 **PROVEĎTE ✓** zkontrolujte virtuální pouze nejdelší přetížení (Pokud je vyžadována rozšíření). Kratší přetížení by měly volat jednoduše prostřednictvím delší přetížení.  
  
 **X nesmí** použít `ref` nebo `out` modifikátory k přetížení členy.  
  
 Některé jazyky nelze vyřešit volání přetížení takto. Kromě toho tyto přetížení obvykle mají úplně jiné sémantiku a pravděpodobně by neměla být přetížení ale dvě samostatné metody místo.  
  
 **X nesmí** , mají přetížení s parametry na stejné pozici a podobné typy, ale s jinou sémantiku.  
  
 **PROVEĎTE ✓** povolit `null` předávané volitelné argumenty.  
  
 **PROVEĎTE ✓** použít člen přetížení než definování členy s výchozí argumenty.  
  
 Výchozí argumenty nejsou kompatibilní se specifikací CLS.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
