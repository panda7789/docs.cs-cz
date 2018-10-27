---
title: Pokyny pro vytváření komponent pro souběžné spouštění
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cedcb20ba12e7c362c60d33dfedfa1882eaa7e7
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50047446"
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>Pokyny pro vytváření komponent pro souběžné spouštění
Postupujte podle následujících obecných pokynů pro vytvoření spravované aplikace nebo komponenty, které jsou určeny pro spuštění vedle sebe:  
  
-   Typ identity svázat konkrétní verze souboru.  
  
     Modul common language runtime typ identity váže na konkrétní verzi pomocí sestavení se silným názvem. Pokud chcete vytvořit aplikaci nebo komponentu pro spuštění vedle sebe, musíte poskytnout všechna sestavení silným názvem. Tím se vytvoří přesný typ identity a zajistí, že všechny rozlišení typu se směřuje do správného souboru. Sestavení se silným názvem obsahuje verzi, jazykovou verzi a informace o vydavateli, který modul runtime používá k vyhledání správného souboru ke splnění požadavků vazby.  
  
-   Používání úložiště podporující verze.  
  
     Modul runtime používá k poskytování úložiště podporující verze globální mezipaměti sestavení. Globální mezipaměť sestavení je nainstalovaný na každém počítači, který používá rozhraní .NET Framework verze aware adresářová struktura. Při instalaci nové verze sestavení, se nepřepíší sestavení nainstalovaná v globální mezipaměti sestavení.  
  
-   Vytvoření aplikace nebo komponenty, na kterém běží izolovaně.  
  
     Aplikace nebo komponenty, na kterém běží izolovaně musí spravovat prostředky, aby nedocházelo ke konfliktům, pokud současně spuštěné dvě instance aplikace nebo komponenty. Struktura souborů specifické pro verzi musíte použít také aplikace nebo komponenty.  
  
## <a name="application-and-component-isolation"></a>Aplikace a komponenty izolace  
 Izolace je jeden klíč k úspěšně návrhu aplikace nebo komponenty pro spuštění vedle sebe. Aplikace nebo komponenta musí spravovat všechny prostředky, zejména souboru vstupně-výstupních operací, izolovaně. Postupujte podle následujících pokynů, abyste měli jistotu, že vaše aplikace nebo komponenty běží izolovaně:  
  
-   Zápis do registru tak konkrétní verzi. Store hodnoty v podregistry nebo klíče, které označuje verzi a sdílet informace nebo stavu mezi verzemi součásti. Díky tomu dvou aplikací nebo součástí, které běží ve stejnou dobu přepsání informace.  
  
-   Ujistěte se, s názvem jádra objekty specifické pro verzi tak, aby se neděje časování. Například časování nastane, pokud dva semafory z dvě verze stejné aplikace čekat na sebe navzájem.  
  
-   Ujistěte se, názvy souborů a adresářů podporující verze. To znamená, že soubor struktury by se neměla spoléhat na informace o verzi.  
  
-   Vytvořte uživatelské účty a skupiny v podobě specifické pro verzi. Uživatelské účty a skupiny vytvořený aplikací by měly být identifikovány verze. Nesdílejte účty uživatelů a skupin mezi službami verze aplikace.  
  
## <a name="installing-and-uninstalling-versions"></a>Instalace a odinstalace verze  
 Když navrhujete aplikaci pro spuštění vedle sebe, dodržujte následující pokyny týkající se instalace a odinstalace verze:  
  
-   Neodstraňujte informace z registru, který může být potřeba jiné aplikace běžící pod jinou verzi rozhraní .NET Framework.  
  
-   Nenahrazují informace v registru, který může být potřeba jiné aplikace běžící pod jinou verzi rozhraní .NET Framework.  
  
-   Nelze zrušit registraci komponenty modelu COM, které může být potřeba jiné aplikace běžící pod jinou verzi rozhraní .NET Framework.  
  
-   Neměňte **InprocServer32** nebo jiné položky registru pro server COM, který již byl registrován.  
  
-   Neodstraňujte uživatelské účty nebo skupiny, které může být potřeba jiné aplikace běžící pod jinou verzi rozhraní .NET Framework.  
  
-   Nepřidávejte nic do registru, který obsahuje cestu k bez označení verze.  
  
## <a name="file-version-number-and-assembly-version-number"></a>Číslo verze souboru a číslo verze sestavení  
 Verze souboru je prostředek systému Win32 verze, která se nepoužívá modul runtime. Obecně platí aktualizujte verzi souboru i pro místní aktualizace. Dva shodné soubory může mít jiný soubor informací o verzi a dvě různé soubory mohou mít stejné informace o verzi souboru.  
  
 Verze sestavení používají modul runtime pro vazby sestavení. Dva identické sestavení pomocí různá čísla verze jsou považovány za dvě různá sestavení modulem runtime.  
  
 [Nástroj Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) umožňuje nahradit sestavení, když pouze čísla verze souboru je novější. Instalační program obecně není možné nainstalovat přes sestavení Pokud číslo verze sestavení je větší.  
  
## <a name="see-also"></a>Viz také  
- [Souběžné spouštění](../../../docs/framework/deployment/side-by-side-execution.md)  
- [Postupy: Povolení a zákaz automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
