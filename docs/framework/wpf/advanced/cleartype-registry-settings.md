---
title: Nastavení registru ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: cacdc47a35bfd197bcac29edc6f7c780d3b8578f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cleartype-registry-settings"></a>Nastavení registru ClearType
Toto téma obsahuje přehled [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] nastavení registru, které jsou používány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
  
<a name="overview"></a>   
## <a name="technology-overview"></a>Přehled technologie  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, které vykreslení text, který se k využívání zařízení zobrazení [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkce zajistit lepší čtení prostředí. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] je technologie softwaru vyvinuté [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] která zlepšuje čitelnost textu na existující monitorů LCD (zobrazí se Crystal kapaliny), například přenosný počítač obrazovky, Pocket PC obrazovky a ploché monitory. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funguje díky přístupu k elementů stripe jednotlivých svislé barev v každé pixelů displeje. Další informace o [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], najdete v části [ClearType přehled](../../../../docs/framework/wpf/advanced/cleartype-overview.md).  
  
 Text, který je vykreslen pomocí [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] může vyskytovat výrazně odlišné při prohlížení na různých zařízeních zobrazení. Například malý počet monitorů implementovat prvky stripe barev v pořadí modré, zelené, red místo častější red, zelená, modrá ( [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) pořadí.  
  
 Text, který je vykreslen pomocí [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] může zobrazit i výrazně odlišné, při zobrazení jednotlivci s různými úrovněmi barva velkých a malých písmen. Některé jednotlivce může rozpoznat drobné rozdíly v barva lépe než jiné.  
  
 V každé z těchto případech [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkce potřeba upravit Chcete-li poskytovat nejlepší čtení prostředí pro každého uživatele.  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Nastavení registru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Určuje čtyři nastavení registru pro řízení [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkce:  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] úroveň|Popisuje úroveň [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] barvu přehlednost.|  
|Úroveň gama|Popisuje úroveň komponentu barev pixelů pro zobrazení zařízení.|  
|Struktura pixelů|Popisuje uspořádání pixelů pro zobrazení zařízení.|  
|Úroveň kontrast textu|Popisuje úroveň kontrast pro zobrazený text.|  
  
 Tato nastavení mají přístup externí konfigurace nástroj, který umí tak, aby odkazovaly identifikovanou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nastavení registru. Tato nastavení taky můžou vytvořit nebo upravit přístup k hodnoty přímo pomocí [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Editor registru.  
  
 Pokud [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nastavení registru (což je výchozí stav), nejsou nastaveny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace dotazy [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] systémové informace parametry vyhlazení nastavení písma.  
  
> [!NOTE]
>  Informace o vytváření výčtů zobrazované názvy zařízení, najdete v článku `SystemParametersInfo` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkce.  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>Úroveň ClearType  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Úroveň umožňuje upravit vykreslování textu na základě barva velkých a malých písmen a dojem jednotlivce. Pro některé jednotlivce vykreslování textu, který používá [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] na nejvyšší úrovni nevytváří nejvhodnější čtení prostředí.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Úroveň je celočíselná hodnota, která rozsah od 0 do 100. Výchozí úroveň je 100, což znamená, že [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] používá funkci maximální elementů stripe barva zobrazovací zařízení. Ale [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] text jako šedé vykreslí nastavena na hodnotu 0. Nastavením [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] úrovni někde mezi 0 a 100, můžete vytvořit pokročilou úroveň, který je vhodný pro jednotlivce barva velkých a malých písmen.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Umístění nastavení registru [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] úroveň je na jednotlivých uživatelských nastavení, která odpovídá konkrétní zobrazovaný název zařízení:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý zobrazovaný název zařízení pro uživatele `ClearTypeLevel` DWORD hodnota je definována. Následující snímek obrazovky ukazuje nastavení editoru registru [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] úroveň.  
  
 ![ClearType nastavení v editoru registru](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslení textu v jednom z buď dva způsoby, s nebo bez aplikace [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]. Pokud je text reprezentován bez [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], jsou označovány jako šedé vykreslování.  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Úroveň gama  
 Úroveň gama odkazuje na nelineární vztah mezi hodnota pixelů a světlostí. Nastavení úrovně gama by měla odpovídat fyzické charakteristiky zobrazovací zařízení; jinak může dojít, narušení ve vykreslené výstupu. Například příliš široké nebo příliš úzké, může se zobrazit testovací nebo barva třásněmi může být uveden na okrajích svislé kořeny glyfů.  
  
 Úroveň gama je celočíselná hodnota, která se pohybuje od 1000 do 2200. Výchozí úroveň je 1900.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Nastavení umístění gama úrovně registru, je nastavení místního počítače, které odpovídá konkrétní zobrazovaný název zařízení:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý zobrazovaný název zařízení pro uživatele `GammaLevel` DWORD hodnota je definována. Následující snímek obrazovky ukazuje nastavení editoru registru gama úroveň.  
  
 ![ClearType nastavení v editoru registru](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>Struktura pixelů  
 Struktura pixelů popisuje typ pixelů, které tvoří zobrazení zařízení. Struktura pixelů je definován jako jeden ze tří typů:  
  
|Typ|Hodnota|Popis|  
|----------|-----------|-----------------|  
|Dvojrozměrném|0|Zobrazovací zařízení nemá žádné struktura pixelů. To znamená, že zdroje světla u každé barvy jsou rovnoměrně oblasti pixelů – tento proces se označuje jako šedé vykreslování. Toto je, jak zobrazit standardní zařízení funguje. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Nikdy se použije u vykresleného textu.|  
|RGB|1|Zobrazovací zařízení má pixelů, které se skládají ze tří rozděluje v následujícím pořadí: červená, zelená a modrá. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] je použita na vykreslovaných text.|  
|BGR|2|Zobrazovací zařízení má pixelů, které se skládají ze tří rozděluje v následujícím pořadí: modrá, zelená a červený. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] je použita na vykreslovaných text. Všimněte si, jak je z typu RGB obrácený pořadí.|  
  
 Struktura pixelů odpovídá na celočíselnou hodnotu rozsahu od 0 do 2. Výchozí úroveň je 0, který reprezentuje strukturu ploché pixelů.  
  
> [!NOTE]
>  Informace o vytváření výčtů zobrazované názvy zařízení, najdete v článku `EnumDisplayDevices` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkce.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Nastavení umístění pro strukturu pixelů registru je nastavení místního počítače, které odpovídá konkrétní zobrazovaný název zařízení:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý zobrazovaný název zařízení pro uživatele `PixelStructure` DWORD hodnota je definována. Následující snímek obrazovky ukazuje nastavení editoru registru pro strukturu pixelů.  
  
 ![ClearType nastavení v editoru registru](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>Úroveň kontrast textu  
 Úroveň kontrast text umožňuje upravit vykreslování textu podle šířky stem glyfů. Úroveň kontrast textu je celočíselná hodnota, která rozsah od 0 do 6 – větší celočíselná hodnota, tím širší stem. Výchozí úroveň je 1.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Nastavení umístění pro úroveň kontrast text registru je na jednotlivých uživatelských nastavení, která odpovídá konkrétní zobrazovaný název zařízení:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý zobrazovaný název zařízení pro uživatele `TextContrastLevel` DWORD hodnota je definována. Následující snímek obrazovky ukazuje nastavení editoru registru pro úroveň kontrast text.  
  
 ![ClearType nastavení v editoru registru](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
## <a name="see-also"></a>Viz také  
 [ClearType – přehled](../../../../docs/framework/wpf/advanced/cleartype-overview.md)  
 [ClearType vyhlazení](https://msdn.microsoft.com/library/dd183433(v=vs.85).aspx)
