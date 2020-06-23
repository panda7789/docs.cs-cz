---
title: Spouštění internetových aplikací v režimu plné důvěryhodnosti
description: Spouštějte intranetové aplikace v úplném vztahu důvěryhodnosti s .NET 3,5 SP1. Aplikace a jejich sestavení knihoven lze spustit jako sestavení s úplným vztahem důvěryhodnosti ze sdílené síťové složky.
ms.date: 03/30/2017
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
ms.openlocfilehash: f4fb3b61e434154b1c7252377c234aeff49f0227
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104592"
---
# <a name="running-intranet-applications-in-full-trust"></a>Spouštění internetových aplikací v režimu plné důvěryhodnosti

Počínaje verzí 3,5 .NET Framework Service Pack 1 (SP1), aplikace a jejich sestavení knihoven lze spustit jako plně důvěryhodná sestavení ze sdílené síťové složky. <xref:System.Security.SecurityZone.MyComputer>legitimace zóny je automaticky přidána do sestavení, která jsou načtena ze sdílené složky v intranetu. Tato legitimace dává těmto sestavením stejnou sadu udělení (což je obvykle úplný vztah důvěryhodnosti) jako sestavení, která jsou umístěna v počítači. Tato funkce se nevztahuje na aplikace ClickOnce ani na aplikace, které jsou navržené pro spouštění na hostiteli.  
  
## <a name="rules-for-library-assemblies"></a>Pravidla pro sestavení knihovny  

Následující pravidla platí pro sestavení, která jsou načtena spustitelným souborem ve sdílené síťové složce:  
  
- Sestavení knihovny se musí nacházet ve stejné složce jako spustitelné sestavení. Sestavení, která se nacházejí v podsložce nebo jsou odkazována na jinou cestu, nemají udělenou sadu udělení úplné důvěryhodnosti.  
  
- Pokud spustitelný soubor zpožděně načte sestavení, musí použít stejnou cestu, která byla použita ke spuštění spustitelného souboru. Pokud je například sdílená \\ \\ *Složka Síťová počítač* \\ *share* namapovaná na písmeno jednotky a spustitelný soubor je spuštěn z této cesty, sestavení, která jsou načtena spustitelným souborem pomocí síťové cesty, nebudou udělena plná důvěryhodnost. Pro zpožděné načtení sestavení v <xref:System.Security.SecurityZone.MyComputer> zóně musí spustitelný soubor použít cestu k písmenu jednotky.  
  
## <a name="restoring-the-former-intranet-policy"></a>Obnovují se předchozí zásady intranetu.  

V dřívějších verzích .NET Framework byly sdílená sestavení udělena <xref:System.Security.SecurityZone.Intranet> legitimace zóny. Bylo nutné zadat zásadu zabezpečení přístupu kódu pro udělení úplné důvěryhodnosti sestavení pro sdílenou složku.  
  
Toto nové chování je výchozím nastavením pro intranetová sestavení. Můžete se vrátit k dřívějšímu chování poskytnutí <xref:System.Security.SecurityZone.Intranet> legitimace nastavením klíče registru, který se vztahuje na všechny aplikace v počítači. Tento proces se liší pro 32 a 64 bitové a počítače:  
  
- Na 32 počítačů Vytvořte pod HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft podklíč \\ . NETFramework klíč v registru systému. Použijte název klíče LegacyMyComputerZone s hodnotou DWORD 1.  
  
- Na 64 počítačů Vytvořte pod HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft podklíč \\ . NETFramework klíč v registru systému. Použijte název klíče LegacyMyComputerZone s hodnotou DWORD 1. V HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft vytvořte stejný podklíč \\ . NETFramework klíč.  
  
## <a name="see-also"></a>Viz také

- [Programování se sestaveními](../../standard/assembly/index.md)
