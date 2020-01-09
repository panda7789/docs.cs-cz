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
ms.openlocfilehash: e7decab042dd1ee36beacb18956e175196cd112c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709280"
---
# <a name="member-overloading"></a>Přetížení člena
Přetížení členů znamená vytvoření dvou nebo více členů na stejném typu, které se liší pouze počtem nebo typem parametrů, ale mají stejný název. Například v následujícím příkladu je přetížená metoda `WriteLine`:  
  
```csharp  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 Vzhledem k tomu, že pouze metody, konstruktory a indexované vlastnosti mohou mít parametry, mohou být přetíženy pouze tyto členy.  
  
 Přetížení je jedním z nejdůležitějších technik pro zlepšení použitelnosti, produktivity a čitelnosti opakovaně použitelných knihoven. Přetížení na základě počtu parametrů umožňuje poskytovat jednodušší verze konstruktorů a metod. Přetížení typu parametru umožňuje použít stejný název člena pro členy, kteří provádějí stejné operace na vybrané sadě různých typů.  
  
 **✓ DO** zkuste použít parametr popisné názvy označíte, výchozí hodnotu použitou kratší přetíženími.  
  
 **X AVOID** nahodile různými názvy parametrů v přetížení. Pokud parametr v jednom přetížení představuje stejný vstup jako parametr v jiném přetížení, musí mít parametry stejný název.  
  
 **X AVOID** nekonzistentní v pořadí parametrů v přetížen členy. Parametry se stejným názvem by měly být ve všech přetíženích ve stejné pozici.  
  
 **✓ DO** zkontrolujte virtuální pouze nejdelší přetížení (Pokud je vyžadována rozšíření). Kratší přetížení by se měla jednoduše volat na delší přetížení.  
  
 **X DO NOT** použít `ref` nebo `out` modifikátory k přetížení členy.  
  
 Některé jazyky nemůžou vyřešit volání přetížení, jako je to. Kromě toho taková přetížení obvykle mají zcela jinou sémantiku a pravděpodobně by neměla být přetížení, ale dvě samostatné metody.  
  
 **X DO NOT** , mají přetížení s parametry na stejné pozici a podobné typy, ale s jinou sémantiku.  
  
 **✓ DO** povolit `null` předávané volitelné argumenty.  
  
 **✓ DO** použít člen přetížení než definování členy s výchozí argumenty.  
  
 Výchozí argumenty nejsou kompatibilní se specifikací CLS.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
