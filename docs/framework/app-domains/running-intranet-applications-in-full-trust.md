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
ms.openlocfilehash: 3c6f58ef5bd96d8a74ce27bb53acd36af005c335
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356781"
---
# <a name="running-intranet-applications-in-full-trust"></a>Spouštění internetových aplikací v režimu plné důvěryhodnosti
Od verze rozhraní .NET Framework verze 3.5, Service Pack 1 (SP1), aplikací a jejich sestavení knihovny můžete spouštět jako plné důvěryhodnosti sestavení ze sdílené síťové složky. <xref:System.Security.SecurityZone.MyComputer> důkaz zóny se automaticky přidá do sestavení, která jsou načtena ze sdílené složky v síti intranet. Tento důkaz poskytuje tyto sestavení, udělení stejné sady (což je obvykle úplný vztah důvěryhodnosti) jako sestavení, které jsou umístěny v počítači. Tato funkce neplatí pro aplikace ClickOnce nebo aplikace, které jsou určená ke spuštění na hostiteli.  
  
## <a name="rules-for-library-assemblies"></a>Pravidla pro sestavení knihovny  
 Následující pravidla platí při sestavení, které jsou načteny spustitelný soubor ve sdílené síťové složce:  
  
-   Sestavení knihovny se musí nacházet ve stejné složce jako spustitelný soubor sestavení. Sestavení, které jsou umístěny v podsložce nebo se odkazuje na jinou cestu nejsou zadané sady udělení plné důvěryhodnosti.  
  
-   Pokud spustitelný soubor zpoždění načte sestavení, musí používat stejnou cestu, která se používá ke spuštění spustitelného souboru. Například pokud sdílenou složku \\ \\ *počítače v síti*\\*sdílet* je namapovaný na písmeno jednotky a spustitelný soubor spouští z cesty, sestavení, která jsou načtena pomocí spustitelného souboru s použitím síťovou cestu neposkytne úplný vztah důvěryhodnosti. Načtení se zpožděním sestavení v <xref:System.Security.SecurityZone.MyComputer> zóny, spustitelný soubor, musíte použít cestu s písmenem jednotky.  
  
## <a name="restoring-the-former-intranet-policy"></a>Obnovení dosavadní intranetu zásad  
 V dřívějších verzích rozhraní .NET Framework byla poskytnuta sdílená sestavení <xref:System.Security.SecurityZone.Intranet> zónu důkaz. Musíte zadat zásady zabezpečení přístupu kódu udělit úplný vztah důvěryhodnosti k sestavení ve sdílené složce.  
  
 Toto chování je výchozí pro sestavení intranetu. Můžete se vrátit dřívějšímu chování poskytování <xref:System.Security.SecurityZone.Intranet> důkaz nastavením klíče registru, který se vztahuje na všechny aplikace v počítači. Tento proces se liší pro 32bitové a 64bitové počítače:  
  
-   Na 32bitové počítače, vytvořte podklíč HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč v registru systému. Použijte název klíče LegacyMyComputerZone s hodnotou DWORD s hodnotou 1.  
  
-   Na 64bitových počítačích, vytvořte podklíč HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč v registru systému. Použijte název klíče LegacyMyComputerZone s hodnotou DWORD s hodnotou 1. Vytvořit podklíč stejné pod HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klíč.  
  
## <a name="see-also"></a>Viz také  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
