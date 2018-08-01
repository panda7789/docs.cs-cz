---
title: Člen přetížení
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c77f08cd573dc40083718b783ae01233ca00766
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573552"
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
  
 **✓ DO** zkuste použít parametr popisné názvy označíte, výchozí hodnotu použitou kratší přetíženími.  
  
 **X AVOID** nahodile různými názvy parametrů v přetížení. Pokud parametr v jedním přetížením představuje stejné vstupu jako parametr v jiné přetížení, parametry musí mít stejný název.  
  
 **X AVOID** nekonzistentní v pořadí parametrů v přetížen členy. Parametry se stejným názvem by se zobrazit ve stejné pozici v všechny přetížení.  
  
 **✓ DO** zkontrolujte virtuální pouze nejdelší přetížení (Pokud je vyžadována rozšíření). Kratší přetížení by měly volat jednoduše prostřednictvím delší přetížení.  
  
 **X DO NOT** použít `ref` nebo `out` modifikátory k přetížení členy.  
  
 Některé jazyky nelze vyřešit volání přetížení takto. Kromě toho tyto přetížení obvykle mají úplně jiné sémantiku a pravděpodobně by neměla být přetížení ale dvě samostatné metody místo.  
  
 **X DO NOT** , mají přetížení s parametry na stejné pozici a podobné typy, ale s jinou sémantiku.  
  
 **✓ DO** povolit `null` předávané volitelné argumenty.  
  
 **✓ DO** použít člen přetížení než definování členy s výchozí argumenty.  
  
 Výchozí argumenty nejsou kompatibilní se specifikací CLS.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
