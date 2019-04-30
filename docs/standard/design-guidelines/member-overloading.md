---
title: Přetížení člena
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: KrzysztofCwalina
ms.openlocfilehash: b13f9e1551aec7e53ba1ac2ed0b9049d46b0a756
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945542"
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
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
