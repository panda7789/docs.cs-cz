---
title: "Pokyny pro vytváření komponent pro souběžné spouštění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 054744612ec54861f675005a27a309e00024b242
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>Pokyny pro vytváření komponent pro souběžné spouštění
Dodržujte následující obecné pokyny k vytvoření spravované aplikace nebo součásti určené pro spuštění vedle sebe:  
  
-   Typ identity vazbu na konkrétní verzi souboru.  
  
     Modul common language runtime sváže identitu typu určitého souboru verze pomocí sestavení se silným názvem. Pokud chcete vytvořit aplikace nebo součásti pro spuštění vedle sebe, musí dát všechna sestavení silným názvem. Tím se vytvoří přesné typ identity a zajistí, že všechny typu řešení směřuje na správný soubor. Sestavení se silným názvem obsahuje verze, jazykové verze a vydavatele informace, které používá modul runtime najít správný soubor ke splnění požadavku vazby.  
  
-   Použijte používající verzi úložiště.  
  
     K poskytování úložiště používající verzi modulu runtime používá globální mezipaměti sestavení. Globální mezipaměť sestavení je používající verzi adresářová struktura nainstalována v každém počítači, který používá rozhraní .NET Framework. Sestavení, které jsou nainstalované v globální mezipaměti sestavení se nepřepíšou při instalaci nové verze této položky assembly.  
  
-   Vytvoření aplikace nebo součásti, které běží izolovaně.  
  
     Aplikace nebo součásti, který spouští v izolaci musí spravovat prostředky, aby nedocházelo ke konfliktům, když dvě instance aplikací nebo součástí běží současně. Aplikace nebo součásti, musíte taky použít struktury specifické pro verzi souborů.  
  
## <a name="application-and-component-isolation"></a>Aplikace a součásti izolace  
 Jednoho klíče na úspěšně návrhu aplikace nebo součásti pro spuštění vedle sebe je izolace. Aplikace nebo součásti musí spravovat všechny prostředky, zejména souboru vstupně-výstupních operací, izolovaně. Postupujte podle těchto pokynů, abyste měli jistotu, že vaše aplikace nebo součásti spouští v izolaci:  
  
-   Zápis do registru způsobem specifické pro verzi. Ukládání hodnot podregistrů nebo klíče, které určují verze a mezi verzemi součásti nesdílí informace o stavu nebo stavu. Tím se zabrání dvě aplikace nebo součásti, které jsou spuštěné ve stejnou dobu ze přepsal informace.  
  
-   Zajistěte objektů s názvem jádra specifické pro verzi, takže časování nedojde. Například časování nastane, když dvě semaforů z dvě verze stejné aplikace čekat na sebe navzájem.  
  
-   Zkontrolujte názvy souborů a adresářů využívající technologii verze. To znamená, že se soubor struktury spoléhají na informace o verzi.  
  
-   Vytvořte uživatelské účty a skupiny způsobem specifické pro verzi. Uživatelské účty a skupiny vytvořené aplikace, mělo by být určené verzí. Nesdílí uživatelské účty a skupiny mezi verzemi aplikace.  
  
## <a name="installing-and-uninstalling-versions"></a>Instalace a odinstalace verze  
 Při navrhování aplikace pro spuštění vedle sebe, dodržujte následující pokyny týkající se instalace a odinstalace verze:  
  
-   Neodstraňujte informace z registru, který může být potřeba pomocí dalších aplikací běžících v rámci jinou verzi rozhraní .NET Framework.  
  
-   Nepřepisovat existující informace v registru, který může být potřeba pomocí dalších aplikací běžících v rámci jinou verzi rozhraní .NET Framework.  
  
-   Nelze zrušit registraci komponenty modelu COM, které může být potřeba pomocí dalších aplikací běžících v rámci jinou verzi rozhraní .NET Framework.  
  
-   Neměňte **InprocServer32** nebo jiné položky registru pro server COM, která již byla zaregistrována.  
  
-   Neodstraňujte uživatelské účty nebo skupiny, které může být potřeba pomocí dalších aplikací běžících v rámci jinou verzi rozhraní .NET Framework.  
  
-   Nepřidávejte nic do registru, který obsahuje cestu bez uvedené verze.  
  
## <a name="file-version-number-and-assembly-version-number"></a>Číslo verze souboru a číslo verze sestavení  
 Verze souboru je prostředek verze Win32, který se nepoužívá modulem runtime. Obecně platí aktualizujte verzi souboru i pro aktualizaci na místě. Dva identické soubory může obsahovat informace o verzi jiný soubor, a dva různé soubory mohou mít stejné informace o verzi souboru.  
  
 Verze sestavení se používá modulem runtime pro sestavení – vazby. Dva identické sestavení pomocí různých čísel verzí jsou považovány za dvě různé sestavení modulem runtime.  
  
 [Nástroj globální mezipaměti sestavení (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) můžete nahradit sestavení při pouze čísla verze souboru je novější. Instalační program obecně instalací sestavení Pokud číslo verze sestavení je větší.  
  
## <a name="see-also"></a>Viz také  
 [Spuštění vedle sebe](../../../docs/framework/deployment/side-by-side-execution.md)  
 [Postupy: povolení a zákaz automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
