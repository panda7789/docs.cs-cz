---
title: Nastavení registru ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: ffc21ca3eed979e9b7cd419f63729d8520a54a5d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720285"
---
# <a name="cleartype-registry-settings"></a>Nastavení registru ClearType
Toto téma obsahuje přehled [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] nastavení registru, které jsou používány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací.  
  
  
<a name="overview"></a>   
## <a name="technology-overview"></a>Přehled technologie  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací, které vykreslují text, který má použít zařízení zobrazení [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkce a zajistit rozšířené čtení prostředí. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] je software technologie vyvinutá společností [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] , který zlepšuje čitelnost textu na existující monitorů LCD (zobrazí se Liquid Crystal), například Notebook obrazovky, obrazovky v prostředí Pocket PC a monitorování plochý. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funguje díky přístupu do jednotlivých svislé barevné prvky stripe v každý pixel displeje. Další informace o [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], naleznete v tématu [ClearType – přehled](../../../../docs/framework/wpf/advanced/cleartype-overview.md).  
  
 Text, který je vykreslen pomocí [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] se může objevit výrazně liší při prohlížení na různá zobrazení zařízení. Například implementovat malý počet monitorů prvky stripe barvy v pořadí modrý, zelená, red spíše než běžné červená, zelená, modrá ( [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) pořadí.  
  
 Text, který je vykreslen pomocí [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] se může zobrazit i výrazně liší, při zobrazení jednotlivci s různými úrovněmi barva citlivosti. Některé jednotlivce dokáže rozpoznat mírné rozdíly v barva lepší než jiné.  
  
 Ve všech těchto případech [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkce je třeba upravit tak, aby poskytují to nejlepší prostředí pro čtení pro jednotlivé uživatele.  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Nastavení registru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Určuje čtyři nastavení registru pro řízení [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkce:  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] úroveň|Popisuje úroveň [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] barva nejasnostem.|  
|Funkce gamma úroveň|Popisuje úroveň složku barvy obrazových bodů pro zobrazovací zařízení.|  
|Struktura pixelů|Popisuje uspořádání pixelů pro zobrazovací zařízení.|  
|Úroveň kontrastu text|Popisuje úroveň kontrastu zobrazeného textu.|  
  
 Tato nastavení je možný přes externí konfigurační nástroj, který ví, jak odkazovat zjištěné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nastavení registru. Tato nastavení také můžou vytvořit nebo upravit přístup k hodnoty přímo s použitím [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Editor registru.  
  
 Pokud [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nastavení registru (což je výchozí stav), nejsou nastaveny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace dotazy [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] systému informace o parametrech pro font smoothing nastavení.  
  
> [!NOTE]
>  Informace o vytváření výčtů zobrazované názvy zařízení, najdete v článku `SystemParametersInfo` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkce.  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>ClearType – úrovně  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Úroveň umožňuje upravit vykreslení textu na základě citlivosti barvu a dojem jednotlivec. Několik jednotlivců, vykreslování textu, který používá [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] na nejvyšší úrovni nevytváří nejlepší prostředí pro čtení.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Úroveň je celočíselnou hodnotu od 0 do 100. Výchozí úroveň je 100, což znamená, že [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] používá maximální funkce prvky stripe barev zobrazení zařízení. Ale [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] úroveň 0 generuje text jako šedé. Tím, že nastavíte [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] úrovně někde mezi 0 a 100, můžete vytvořit pokročilou úroveň, který je vhodný pro jednotlivce barva citlivosti.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Nastavení umístění registru [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] úroveň je nastavení jednotlivých uživatelů, která odpovídá názvu displeje konkrétního zařízení:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý zobrazovaný název zařízení pro uživatele `ClearTypeLevel` je definována hodnota DWORD. Následující snímek obrazovky ukazuje nastavení editoru registru [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] úroveň.  
  
 ![Nastavení v editoru registru ClearType](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslení textu v obou dvou režimech a nemusíte aplikace [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]. Když text je vykreslen bez [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], jsou označovány jako šedé vykreslování.  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Funkce gamma úroveň  
 Úroveň funkce gamma odkazuje na nelineárních vztah mezi hodnotami pixelů a světelnost. Nastavení úrovně gama by měl odpovídat fyzické charakteristiky zobrazovací zařízení; v opačném případě může dojít k narušení vykresleného výstupu. Například test může být příliš široké nebo příliš úzký, nebo barva třásněmi mohou zobrazit na okraji svislé kořeny glyphs.  
  
 Úroveň funkce gamma je celočíselná hodnota od 1 000 až 2200. Výchozí úroveň je 1900.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Nastavení umístění funkce gamma úrovně registru je nastavení místního počítače, který odpovídá konkrétní zobrazovaný název zařízení:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý zobrazovaný název zařízení pro uživatele `GammaLevel` je definována hodnota DWORD. Následující snímek obrazovky ukazuje nastavení Editor registru pro úroveň funkce gamma.  
  
 ![Nastavení v editoru registru ClearType](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>Struktura pixelů  
 Struktura pixel popisuje typ v pixelech, které tvoří zobrazovací zařízení. Struktura pixel je definován jako jeden ze tří typů:  
  
|Typ|Hodnota|Popis|  
|----------|-----------|-----------------|  
|Paušální|0|Zobrazovací zařízení nemá žádné struktura pixelů. To znamená, že zdroje světla u každé barvy jsou rovnoměrně v oblasti pixel – to se označuje jako šedé vykreslování. To je, jak se standardní zobrazí zařízení funguje. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nikdy použita na vykreslený text.|  
|RGB|1|Zařízení má pixelů, které se skládají z tři pruhy v následujícím pořadí: červené, zelené a modré. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] platí pro vykreslený text.|  
|BGR|2|Zařízení má pixelů, které se skládají z tři pruhy v následujícím pořadí: modrý, zelené a červený. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] platí pro vykreslený text. Všimněte si, jak je obrácený pořadí z typu RGB.|  
  
 Struktura pixel odpovídá na celočíselnou hodnotu od 0 do 2. Výchozí úroveň je 0, která reprezentuje strukturu plochých pixelů.  
  
> [!NOTE]
>  Informace o vytváření výčtů zobrazované názvy zařízení, najdete v článku `EnumDisplayDevices` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkce.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Nastavení umístění pro strukturu pixel registru je nastavení místního počítače, který odpovídá názvu displeje konkrétního zařízení:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý zobrazovaný název zařízení pro uživatele `PixelStructure` je definována hodnota DWORD. Následující snímek obrazovky ukazuje nastavení Editor registru pro strukturu pixelů.  
  
 ![Nastavení v editoru registru ClearType](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>Úroveň kontrastu text  
 Úroveň kontrastu text můžete upravit vykreslování textu podle šířky stem glyfů. Úroveň kontrastu text je celočíselnou hodnotu od 0 do 6 – Čím větší celočíselná hodnota, čím širší stem. Výchozí úroveň je 1.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Nastavení umístění pro úroveň kontrastu text registru je nastavení jednotlivých uživatelů, která odpovídá názvu displeje konkrétního zařízení:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý zobrazovaný název zařízení pro uživatele `TextContrastLevel` je definována hodnota DWORD. Následující snímek obrazovky ukazuje nastavení Editor registru pro úroveň kontrastu text.  
  
 ![Nastavení v editoru registru ClearType](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
## <a name="see-also"></a>Viz také:
- [ClearType – přehled](../../../../docs/framework/wpf/advanced/cleartype-overview.md)
- [ClearType – vyhlazení](/windows/desktop/gdi/cleartype-antialiasing)
