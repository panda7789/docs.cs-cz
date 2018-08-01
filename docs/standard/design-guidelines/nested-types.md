---
title: Vnořené typy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c0eca851746899654636d36dce679acffc07ef0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573656"
---
# <a name="nested-types"></a>Vnořené typy
Vnořené typy je typem definovaným v rámci oboru jiného typu, který se nazývá nadřazených typů. Vnořené typy má přístup do všech členů jeho nadřazených typů. Například má přístup k privátním pole definovaná v nadřazených typů a chráněné polí definovaných ve všech nadřazených členů nadřazených typů.  
  
 Obecně platí vnořené typy měli šetřit. Tady je několik důvodů pro tento. Někteří vývojáři se plně s koncept. Tyto vývojáři může například máte problémy s syntaxe deklarace proměnné vnořené typy. Vnořené typy jsou také velmi úzce spojeny s jejich nadřazených typů a jako takový nejsou vhodné jako typy pro obecné účely.  
  
 Vnořené typy jsou nejvhodnější pro modelování podrobnosti implementace jejich nadřazených typů. Koncový uživatel by měl obvykle nemusí deklarujte proměnné vnořené typy a téměř žádné musí mít explicitně instance vnořené typy. Enumerátor kolekce může být například vnořené typ této kolekce. Výčty jsou obvykle mohl vytvořit jeho instanci názvy jejich nadřazených typů a mnoha jazycích nepodporují příkazu foreach, enumerátor proměnné zřídka mají deklarovat koncovým uživatelem.  
  
 **✓ DO** použití vnořené typy vztah mezi vnořené typy a jeho vnější typ tak, aby člen usnadnění sémantika je žádoucí.  
  
 **X DO NOT** použití veřejného vnořené typy jako logické seskupení vytvořit; pomocí oborů názvů pro tuto.  
  
 **X AVOID** veřejně vystaven vnořené typy. Jedinou výjimkou je, pokud proměnné vnořené typy potřeba deklarovat pouze ve výjimečných případech, například vytvoření podtřídy či jiné scénáře vlastní nastavení.  
  
 **X DO NOT** použijte vnořené typy, pokud typ je pravděpodobně bude odkazovat mimo nadřazeného typu.  
  
 Například výčet předaný metodě definovaný pro třídu nesmí být definována jako typ vnořené v třídě.  
  
 **X DO NOT** použít vnořené typy, pokud je nutné vytvořit instanci kódem na straně klienta.  Pokud typ má konstruktor public, ho měli pravděpodobně není nelze vnořit.  
  
 Pokud typ se dá vytvořit instance, která zdá se, že k označení, typ je na místě v rozhraní framework svoje vlastní (můžete ji vytvořit, s ním pracovat a zrušení bez někdy pomocí vnější typu) a proto by neměl být vnořený. Vnitřní typy by neměly znovu široce mimo vnější typu bez žádný vztah jakékoli vnější typu.  
  
 **X DO NOT** definovat vnořené typy jako člen rozhraní. Mnoho jazyků nepodporují takové konstrukce.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
