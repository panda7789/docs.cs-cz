---
title: Spouštění internetových aplikací v režimu plné důvěryhodnosti
ms.date: 03/30/2017
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8731e90a66c20f06e8afcd7458349cbc0b93484
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084099"
---
# <a name="running-intranet-applications-in-full-trust"></a>Spouštění internetových aplikací v režimu plné důvěryhodnosti
Od verze rozhraní .NET Framework verze 3.5 Service Pack 1 (SP1), aplikací a jejich sestavení knihovny může běžet jako sestavení úplného vztahu důvěryhodnosti ze sdílené síťové složky. <xref:System.Security.SecurityZone.MyComputer> legitimace zóny se automaticky přidá do sestavení, která jsou načtena ze sdílené složky v síti intranet. Tato legitimace poskytuje tato sestavení, které stejná sada udělení oprávnění (což je obvykle úplný vztah důvěryhodnosti) jako sestavení, které jsou umístěny v počítači. Tato funkce se nedá použít pro aplikace ClickOnce nebo k aplikacím, které jsou navrženy pro spouštění na hostiteli.  
  
## <a name="rules-for-library-assemblies"></a>Pravidla pro sestavení knihovny  
 Následující pravidla platí pro sestavení, která jsou načtená spustitelným do sdílené síťové složky:  
  
-   Sestavení knihovny se musí nacházet ve stejné složce jako spustitelného sestavení. Sestavení, které jsou umístěny v podsložce nebo se odkazuje na jinou cestu nejsou zadané sady udělení úplného vztahu důvěryhodnosti.  
  
-   Pokud spustitelný soubor zpoždění načte sestavení, musí používat stejnou cestu, která byla použita pro spuštění spustitelného souboru. Například pokud sdílenou složku \\ \\ *počítače v síti*\\*sdílet* je namapována na písmeno jednotky a ke spustitelnému souboru spustit z této cesty, sestavení, která jsou načtena pomocí spustitelného souboru pomocí cesty sítě nesmí být udělena úplná důvěryhodnost. Pro zpoždění načtení sestavení <xref:System.Security.SecurityZone.MyComputer> zóny, spustitelný soubor musíte použít cestu s písmenem jednotky.  
  
## <a name="restoring-the-former-intranet-policy"></a>Obnovení zásad bývalé intranetu  
 V dřívějších verzích rozhraní .NET Framework byla udělena sdílená sestavení <xref:System.Security.SecurityZone.Intranet> legitimace zóny. Musíte zadat zásady zabezpečení přístupu kódu udělit úplný vztah důvěryhodnosti k sestavení ve sdílené složce.  
  
 Toto nové chování je výchozí nastavení pro intranet sestavení. Můžete se vrátit k předchozí chování poskytování <xref:System.Security.SecurityZone.Intranet> důkazy nastavením klíče registru, který se vztahuje na všechny aplikace na počítači. Tento proces se liší pro 32bitové a 64bitové počítače:  
  
-   Na 32bitových počítačích, vytvořte podklíč HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíče v registru systému. Použijte název klíče LegacyMyComputerZone s hodnotou DWORD 1.  
  
-   Na 64bitových počítačích, vytvořte podklíč HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíče v registru systému. Použijte název klíče LegacyMyComputerZone s hodnotou DWORD 1. Vytvořit podklíč stejné pod HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klíč.  
  
## <a name="see-also"></a>Viz také:

- [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
