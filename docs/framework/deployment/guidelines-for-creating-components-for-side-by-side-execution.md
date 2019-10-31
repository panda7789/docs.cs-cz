---
title: Pokyny pro vytváření komponent pro souběžné spouštění
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
ms.openlocfilehash: 42d0e2d85517d4a8fb443db9b63e6b893267caca
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121590"
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>Pokyny pro vytváření komponent pro souběžné spouštění
Pokud chcete vytvořit spravované aplikace nebo komponenty navržené pro souběžné spouštění, postupujte podle těchto obecných pokynů:  
  
- Vázání typu identity na určitou verzi souboru.  
  
     Modul CLR (Common Language Runtime) váže identitu typu na konkrétní verzi souboru pomocí sestavení se silným názvem. Chcete-li vytvořit aplikaci nebo komponentu pro souběžné spouštění, musíte všem sestavením poskytnout silný název. Tím se vytvoří přesná identita typu a zajistí se, že jakékoliv rozlišení typu bude směrováno na správný soubor. Sestavení se silným názvem obsahuje informace o verzi, jazykové verzi a vydavateli, které modul runtime používá k vyhledání správného souboru pro splnění požadavku vazby.  
  
- Použijte úložiště podporující verzi.  
  
     Modul runtime používá globální mezipaměť sestavení (GAC) k poskytování úložiště zohledňující verzi. Globální mezipaměť sestavení (GAC) je adresářová struktura s podporou verzí nainstalovaná na každém počítači, který používá .NET Framework. Sestavení nainstalovaná v globální mezipaměti sestavení nejsou při instalaci nové verze tohoto sestavení přepsána.  
  
- Vytvořte aplikaci nebo komponentu, která se spouští izolovaně.  
  
     Aplikace nebo komponenta, která je spuštěna v izolaci, musí spravovat prostředky, aby nedocházelo ke konfliktům při současném spuštění dvou instancí aplikace nebo komponenty. Aplikace nebo komponenta musí také používat strukturu souborů specifickou pro danou verzi.  
  
## <a name="application-and-component-isolation"></a>Izolace aplikací a komponent  
 Jeden klíč k úspěšnému navrhování aplikace nebo komponenty pro souběžné spouštění je izolace. Aplikace nebo komponenta musí spravovat všechny prostředky, zejména v/v souborů, a to izolovaným způsobem. Postupujte podle těchto pokynů, abyste se ujistili, že se aplikace nebo komponenta spouští izolovaně:  
  
- Zapište do registru způsobem, který je specifický pro verzi. Ukládejte hodnoty v podregistrech nebo klíčích, které označují verzi, a nesdílejte informace nebo stav mezi verzemi součásti. Tím se zabrání současnému spuštění dvou aplikací nebo komponent od přepsání informací.  
  
- Nastavte pojmenované objekty jádra jako specifické pro verzi, aby nedocházelo ke konfliktu časování. Například konflikt časování nastane, když dva semafory ze dvou různých verzí stejné aplikace navzájem čekají.  
  
- Vytváření názvů souborů a adresářů, které podporují verzi To znamená, že struktury souborů by měly spoléhat na informace o verzi.  
  
- Vytvořte uživatelské účty a skupiny způsobem, který je specifický pro verzi. Uživatelské účty a skupiny vytvořené aplikací by měly být označeny verzí. Nesdílejte uživatelské účty a skupiny mezi verzemi aplikace.  
  
## <a name="installing-and-uninstalling-versions"></a>Instalace a odinstalace verzí  
 Při navrhování aplikace pro souběžné spouštění postupujte podle těchto pokynů týkajících se instalace a odinstalace verzí:  
  
- Neodstraňujte informace z registru, které mohou být vyžadovány jinými aplikacemi spuštěnými v jiné verzi .NET Framework.  
  
- Neměňte informace v registru, které mohou být vyžadovány jinými aplikacemi spuštěnými v jiné verzi .NET Framework.  
  
- Zrušte registraci komponent modelu COM, které mohou být vyžadovány jinými aplikacemi spuštěnými v jiné verzi .NET Framework.  
  
- Neměňte **InprocServer32** nebo jiné položky registru pro server com, který je už zaregistrovaný.  
  
- Neodstraňujte uživatelské účty nebo skupiny, které mohou být vyžadovány jinými aplikacemi spuštěnými v jiné verzi .NET Framework.  
  
- Nepřidávejte do registru cokoli, co obsahuje cestu s neverzí.  
  
## <a name="file-version-number-and-assembly-version-number"></a>Číslo verze souboru a číslo verze sestavení  
 Verze souboru je prostředek verze Win32, který není používán modulem runtime. Obecně platí, že aktualizujete verzi souboru i pro místní aktualizaci. Dva identické soubory mohou mít různé informace o verzi souboru a dva různé soubory mohou mít stejné informace o verzi souboru.  
  
 Verze sestavení je používána modulem runtime pro vazby sestavení. Dvě identická sestavení s různými čísly verze jsou zpracována jako dvě různá sestavení modulem runtime.  
  
 [Nástroj Global Assembly Cache Tool (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) umožňuje nahradit sestavení pouze v případě, že je novější pouze číslo verze souboru. Instalační program se obecně nenainstaluje přes sestavení, pokud číslo verze sestavení není větší.  
  
## <a name="see-also"></a>Viz také:

- [Souběžné spouštění](side-by-side-execution.md)
- [Postupy: Povolení a zákaz automatického přesměrování vazby](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
