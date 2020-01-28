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
ms.openlocfilehash: c9cb178e838aab99c22089b527a6bd2e86b325de
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727837"
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

 ✔️ se pokuste použít názvy popisných parametrů k označení výchozí hodnoty používané kratšími přetíženími.

 ❌ v případě přetížení vyhnout proměnlivým názvům parametrů. Pokud parametr v jednom přetížení představuje stejný vstup jako parametr v jiném přetížení, musí mít parametry stejný název.

 ❌ vyhnout nekonzistenci v pořadí parametrů v přetížených členech. Parametry se stejným názvem by měly být ve všech přetíženích ve stejné pozici.

 ✔️ UDĚLAT jenom nejdelší přetížený virtuální (Pokud se vyžaduje rozšiřitelnost). Kratší přetížení by se měla jednoduše volat na delší přetížení.

 ❌ nepoužívejte `ref` nebo `out` modifikátory pro přetížení členů.

 Některé jazyky nemůžou vyřešit volání přetížení, jako je to. Kromě toho taková přetížení obvykle mají zcela jinou sémantiku a pravděpodobně by neměla být přetížení, ale dvě samostatné metody.

 ❌ neobsahují přetížení s parametry na stejné pozici a podobných typech ještě s různou sémantikou.

 ✔️ povolit, aby se `null` předala pro volitelné argumenty.

 ✔️ použít přetížení členů namísto definování členů s výchozími argumenty.

 Výchozí argumenty nejsou kompatibilní se specifikací CLS.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
