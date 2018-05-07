---
title: Názvy parametrů
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed6b96bb05c52de4bfd8b6ad6b972c9d22ca66da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="naming-parameters"></a>Názvy parametrů
Nad rámec zřejmé čitelnosti důvod, proč je důležité postupujte podle pokynů pro názvy parametrů, protože parametry jsou zobrazeny v dokumentaci a v návrháři, když nástrojů visual návrhu poskytují Intellisense a třída procházení funkce.  
  
 **PROVEĎTE ✓** použít camelCasing v názvech parametrů.  
  
 **PROVEĎTE ✓** použít parametr popisné názvy.  
  
 **✓ ZVAŽTE** pomocí názvů založených na parametr význam, nikoli typ parametru.  
  
### <a name="naming-operator-overload-parameters"></a>Názvy parametrů přetížení operátoru  
 **PROVEĎTE ✓** použít `left` a `right` pro názvy parametrů přetížení binární operátor Pokud neexistuje žádný význam na parametry.  
  
 **PROVEĎTE ✓** použít `value` pro unární operátor přetížení názvy parametrů, pokud neexistuje žádný význam na parametry.  
  
 **✓ ZVAŽTE** smysluplný názvy pro operátor přetížení parametry, pokud tento postup zvětší významné zlepšení.  
  
 **X nesmí** používání zkratky nebo číselné indexů pro operátor přetížení názvy parametrů.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
