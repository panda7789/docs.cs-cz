---
title: Přetížení člena
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
ms.openlocfilehash: 2127497d294cbfd4e1bb24d033f432378627ff13
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208228"
---
# <a name="member-overloading"></a>Přetížení člena
Přetížení člena znamená, že vytvoření dvou nebo více členů na stejný typ, který se liší pouze velikostí číslo nebo typ parametrů, ale mají stejný název. Například v následujícím příkladu `WriteLine` přetížené metody:  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 Protože pouze metody, konstruktory a indexované vlastnosti mohou mít parametry, mohou být přetíženy pouze ty členy.  
  
 Přetěžování je jedním z nejdůležitějších technik pro vylepšení použitelnosti, produktivitu a čitelnost opakovaně použitelné knihovny. Přetížení pro počet parametrů umožňuje poskytují jednodušší verze konstruktorů a metod. Přetížení u parametru typu umožňuje použití stejného názvu členu pro provádění operací identické na vybrané sadě různé typy členů.  
  
 **✓ DO** zkuste použít parametr popisné názvy označíte, výchozí hodnotu použitou kratší přetíženími.  
  
 **X AVOID** nahodile různými názvy parametrů v přetížení. Pokud parametr v jedním přetížením představuje stejný vstup jako parametr v jiné přetížení, parametry, by měly být stejné.  
  
 **X AVOID** nekonzistentní v pořadí parametrů v přetížen členy. Parametry se stejným názvem, by se zobrazit na stejné pozici v všechna přetížení.  
  
 **✓ DO** zkontrolujte virtuální pouze nejdelší přetížení (Pokud je vyžadována rozšíření). Kratší přetížení by měly volat pouze prostřednictvím delší přetížení.  
  
 **X DO NOT** použít `ref` nebo `out` modifikátory k přetížení členy.  
  
 Některé jazyky nejde vyřešit volání přetížení následujícím způsobem. Kromě toho takovými přetíženími obvykle mít úplně odlišnou sémantiku a pravděpodobně by neměl být přetížení, ale dvě samostatné metody místo.  
  
 **X DO NOT** , mají přetížení s parametry na stejné pozici a podobné typy, ale s jinou sémantiku.  
  
 **✓ DO** povolit `null` předávané volitelné argumenty.  
  
 **✓ DO** použít člen přetížení než definování členy s výchozí argumenty.  
  
 Výchozí argumenty nejsou kompatibilní se Specifikací CLS.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)  
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
