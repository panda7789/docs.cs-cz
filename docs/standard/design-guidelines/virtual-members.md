---
title: Virtuální členové
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 8ed519a01162056151d8ae6398c0d06495911afd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743525"
---
# <a name="virtual-members"></a>Virtuální členové
Virtuální členy lze přepsat, čímž se mění chování podtřídy. Jsou poměrně podobné zpětným voláním z důvodu rozšiřitelnosti, kterou poskytují, ale jsou lepší v souvislosti s výkonem spuštění a spotřebou paměti. Virtuální členové také ve scénářích, které vyžadují vytvoření speciálního druhu stávajícího typu (specializace), mají větší přirozený charakter.

 Virtuální členové provádějí lepší než zpětná volání a události, ale neprovádějí lepší než virtuální metody.

 Hlavní nevýhodou virtuálních členů je, že chování virtuálního člena lze upravit pouze v době kompilace. Chování zpětného volání lze upravit za běhu.

 Virtuální členové, například zpětná volání (a možná více než zpětná volání), jsou nákladné pro návrh, testování a údržbu, protože jakékoli volání virtuálního člena lze přepsat nepředvídatelným způsobem a může spustit libovolný kód. K jasnému definování kontraktů virtuálních členů se obvykle vyžaduje mnohem více úsilí, takže náklady na jejich navrhování a dokumentaci jsou vyšší.

 ❌ nevytvářejte členy Virtual, pokud nemáte dobrý důvod k tomu, abyste se dozvěděli o všech nákladech souvisejících s návrhem, testováním a údržbou virtuálních členů.

 Virtuální členové jsou méně striktní z hlediska změn, které je možné v nich provést bez narušení kompatibility. Jsou také pomalejší než nevirtuální členové, většinou protože volání virtuálních členů nejsou vložena.

 ✔️ Zvažte omezení rozšiřitelnosti jenom na to, co je nezbytně nutné.

 ✔️ preferovat chráněnou přístupnost prostřednictvím veřejné dostupnosti pro virtuální členy. Veřejné členy by měli poskytnout rozšíření (v případě potřeby) voláním do chráněného virtuálního člena.

 Veřejné členy třídy by měli poskytnout správnou sadu funkcí pro přímé spotřebitele této třídy. Virtuální členové jsou navrženi pro přepsání v podtříd a chráněná přístupnost je skvělým způsobem pro vymezení všech virtuálních bodů rozšiřitelnosti na místo, kde je lze použít.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
