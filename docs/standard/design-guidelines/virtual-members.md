---
title: Virtuální členové
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 2c1e6d9aeafa1c9d7ee4b0c2c626b6fd7be6cf99
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708968"
---
# <a name="virtual-members"></a>Virtuální členové
Virtuální členy lze přepsat, čímž se mění chování podtřídy. Jsou poměrně podobné zpětným voláním z důvodu rozšiřitelnosti, kterou poskytují, ale jsou lepší v souvislosti s výkonem spuštění a spotřebou paměti. Virtuální členové také ve scénářích, které vyžadují vytvoření speciálního druhu stávajícího typu (specializace), mají větší přirozený charakter.  
  
 Virtuální členové provádějí lepší než zpětná volání a události, ale neprovádějí lepší než virtuální metody.  
  
 Hlavní nevýhodou virtuálních členů je, že chování virtuálního člena lze upravit pouze v době kompilace. Chování zpětného volání lze upravit za běhu.  
  
 Virtuální členové, například zpětná volání (a možná více než zpětná volání), jsou nákladné pro návrh, testování a údržbu, protože jakékoli volání virtuálního člena lze přepsat nepředvídatelným způsobem a může spustit libovolný kód. K jasnému definování kontraktů virtuálních členů se obvykle vyžaduje mnohem více úsilí, takže náklady na jejich navrhování a dokumentaci jsou vyšší.  
  
 **X DO NOT** zkontrolujte virtuální členy, pokud máte dobrý důvod k tomu a jste si vědomi veškeré náklady související s návrh, testování a údržbě virtuální členy.  
  
 Virtuální členové jsou méně striktní z hlediska změn, které je možné v nich provést bez narušení kompatibility. Jsou také pomalejší než nevirtuální členové, většinou protože volání virtuálních členů nejsou vložena.  
  
 **✓ CONSIDER** omezení rozšiřitelnost pouze co je to nezbytně nutné.  
  
 **✓ DO** raději chráněné usnadnění přes veřejnou dostupnost pro virtuální členy. Veřejné členy by měli poskytnout rozšíření (v případě potřeby) voláním do chráněného virtuálního člena.  
  
 Veřejné členy třídy by měli poskytnout správnou sadu funkcí pro přímé spotřebitele této třídy. Virtuální členové jsou navrženi pro přepsání v podtříd a chráněná přístupnost je skvělým způsobem pro vymezení všech virtuálních bodů rozšiřitelnosti na místo, kde je lze použít.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
