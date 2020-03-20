---
title: Pokyny pro vytváření komponent pro souběžné spouštění
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
ms.openlocfilehash: 42d0e2d85517d4a8fb443db9b63e6b893267caca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121590"
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>Pokyny pro vytváření komponent pro souběžné spouštění
Chcete-li vytvořit spravované aplikace nebo součásti určené pro souběžné provádění, postupujte podle těchto obecných pokynů:  
  
- Identita typu vazby na určitou verzi souboru.  
  
     Běžný jazyk runtime váže identitu typu na konkrétní verzi souboru pomocí sestavení se silným názvem. Chcete-li vytvořit aplikaci nebo součást pro souběžné spuštění, musíte dát všem sestavením silný název. Tím se vytvoří přesná identita typu a zajistí, že jakékoli rozlišení typu je směrováno na správný soubor. Sestavení se silným názvem obsahuje informace o verzi, jazykové verzi a vydavateli, které za běhu používá k vyhledání správného souboru ke splnění požadavku na vazbu.  
  
- Používejte úložiště podporující verzi.  
  
     Runtime používá globální mezipaměti sestavení k poskytování úložiště s informacemi o verzi. Globální mezipaměť sestavení je adresářová struktura s vědomím verze nainstalovaná v každém počítači, který používá rozhraní .NET Framework. Sestavení nainstalovaná v globální mezipaměti sestavení nejsou přepsána při instalaci nové verze tohoto sestavení.  
  
- Vytvořte aplikaci nebo součást, která běží izolovaně.  
  
     Aplikace nebo součást, která běží izolovaně, musí spravovat prostředky, aby se zabránilo konfliktům, když jsou současně spuštěny dvě instance aplikace nebo součásti. Aplikace nebo součást musí také používat strukturu souborů specifickou pro verzi.  
  
## <a name="application-and-component-isolation"></a>Izolace aplikací a komponent  
 Jedním klíčem k úspěšnému návrhu aplikace nebo součásti pro souběžné spuštění je izolace. Aplikace nebo součást musí spravovat všechny prostředky, zejména vstupně-va souboru, izolovaně. Postupujte podle následujících pokynů a ujistěte se, že vaše aplikace nebo součást běží izolovaně:  
  
- Zapisovat do registru způsobem specifickým pro verzi. Uklápěte hodnoty do podregistrů nebo klíčů, které označují verzi, a nesdílejte informace ani stav mezi verzemi komponenty. Tím zabráníte přepsání informací dvěma aplikacím nebo součástem současně.  
  
- Vytvořte pojmenované objekty jádra specifické pro verzi tak, aby nedošlo ke spor. Například spor nastane, když dva semafory ze dvou verzí stejné aplikace čekat na sebe.  
  
- Vytvořte názvy souborů a adresářů pro uvědomění si verze. To znamená, že struktury souborů by měly spoléhat na informace o verzi.  
  
- Vytvořte uživatelské účty a skupiny způsobem specifickým pro verzi. Uživatelské účty a skupiny vytvořené aplikací by měly být identifikovány podle verze. Nesdílejte uživatelské účty a skupiny mezi verzemi aplikace.  
  
## <a name="installing-and-uninstalling-versions"></a>Instalace a odinstalace verzí  
 Při navrhování aplikace pro souběžné spuštění postupujte podle následujících pokynů týkajících se instalace a odinstalace verzí:  
  
- Neodstraňujte informace z registru, které mohou být potřebné jinými aplikacemi spuštěnými v rámci jiné verze rozhraní .NET Framework.  
  
- Nenahrazujte informace v registru, které mohou být potřebné jinými aplikacemi spuštěnými v rámci jiné verze rozhraní .NET Framework.  
  
- Neodhlašovat součásti modelu COM, které mohou být potřebné jinými aplikacemi spuštěnými v rámci jiné verze rozhraní .NET Framework.  
  
- Neměňte **inprocServer32** nebo jiné položky registru pro server COM, který již byl zaregistrován.  
  
- Neodstraňujte uživatelské účty nebo skupiny, které mohou být potřebné jinými aplikacemi spuštěnými v rámci jiné verze rozhraní .NET Framework.  
  
- Nepřidávejte nic do registru, který obsahuje cestu bez verze.  
  
## <a name="file-version-number-and-assembly-version-number"></a>Číslo verze souboru a číslo verze sestavení  
 Verze souboru je prostředek verze win32, který není používán runtime. Obecně platí, že aktualizaci verze souboru i pro aktualizaci na místě. Dva identické soubory mohou mít různé informace o verzi souboru a dva různé soubory mohou mít stejné informace o verzi souboru.  
  
 Verze sestavení se používá za běhu pro vazbu sestavení. Dvě identické sestavení s různými čísly verzí jsou považovány za dvě různá sestavení za běhu.  
  
 Nástroj [globální mezipaměti sestavení (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) umožňuje nahradit sestavení, pokud je novější pouze číslo verze souboru. Instalační program se obvykle neinstaluje přes sestavení, pokud není číslo verze sestavení větší.  
  
## <a name="see-also"></a>Viz také

- [Souběžné spouštění](side-by-side-execution.md)
- [Postupy: Povolení a zákaz automatického přesměrování vazby](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
