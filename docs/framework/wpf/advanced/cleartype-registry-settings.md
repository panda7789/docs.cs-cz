---
title: Nastavení registru ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: 2104cb4e853888efffe6b289ac1400530be25473
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015600"
---
# <a name="cleartype-registry-settings"></a>Nastavení registru ClearType
Toto téma poskytuje přehled nastavení registru Microsoft ClearType používaných aplikacemi WPF.  

<a name="overview"></a>   
## <a name="technology-overview"></a>Přehled technologie  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikace, které vykreslují text na zobrazovací zařízení, používají funkce technologie ClearType k zajištění vylepšeného prostředí pro čtení. ClearType je softwarová technologie vyvinutá Microsoftem, která vylepšuje čitelnost textu v existujících LCDs (Liquid Crystal displeje), jako jsou obrazovky přenosné počítače, obrazovky Pocket PC a monitor plochých panelů. Technologie ClearType funguje tak, že přistupuje k jednotlivým prvkům svislého barevného pruhu v každém pixelu obrazovky LCD. Další informace o technologii ClearType najdete v tématu [Přehled technologie ClearType](cleartype-overview.md).  
  
 Text vykreslený pomocí technologie ClearType se může při zobrazení na různých displejích výrazně lišit. Například malý počet monitorů implementuje prvky barevného pruhu v modrém, zeleném a červeném pořadí, nikoli v běžnější červené, zelené, modré ( [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) objednávce.  
  
 Text vykreslený pomocí technologie ClearType se může také výrazně lišit při prohlížení jednotlivci, kteří mají různou úroveň citlivosti barev. Někteří jednotlivci mohou detekovat mírné rozdíly v barvě lépe než jiné.  
  
 V každém z těchto případů je potřeba upravit funkce technologie ClearType tak, aby poskytovaly nejlepší možnosti pro čtení jednotlivých jednotlivců.  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Nastavení registru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Určuje čtyři nastavení registru pro řízení funkcí ClearType:  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|Úroveň ClearType|Popisuje úroveň srozumitelnosti barvy pro technologii ClearType.|  
|Úroveň gamma|Popisuje úroveň složky pixel Color pro zobrazovací zařízení.|  
|Pixel – struktura|Popisuje uspořádání pixelů pro zobrazovací zařízení.|  
|Úroveň kontrastu textu|Popisuje úroveň kontrastu zobrazeného textu.|  
  
 K těmto nastavením může mít přístup externí konfigurační nástroj, který ví, jak odkazovat na identifikované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nastavení registru ClearType. Tato nastavení se dají vytvářet nebo upravovat taky tak, že se přistupují k hodnotám přímo pomocí Editoru registru Windows.  
  
 Pokud nastavení registru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ClearTypenejsounastavená(cožjevýchozístav),aplikacesedotazujenainformaceoparametrechsystémuWindowspronastavení[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]vyhlazení písma.  
  
> [!NOTE]
> Informace o vytváření výčtu zobrazovaných názvů zařízení najdete ve `SystemParametersInfo` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkci.  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>Úroveň ClearType  
 Úroveň ClearType umožňuje upravit vykreslování textu na základě citlivosti barev a vnímání jednotlivce. V případě některých jednotlivců neprodukuje vykreslování textu, který využívá technologii ClearType na nejvyšší úrovni, nejlepší možnosti pro čtení.  
  
 Úroveň ClearType je celočíselná hodnota, která je v rozsahu od 0 do 100. Výchozí úroveň je 100, což znamená, že technologie ClearType používá maximální schopnost prvků barevného pruhu zobrazovacího zařízení. Úroveň technologie ClearType však 0 vykresluje text jako šedý stupnici. Nastavením úrovně ClearType v rozmezí od 0 do 100 můžete vytvořit pokročilou úroveň, která je vhodná pro Citlivost barvy jednotlivce.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Umístění nastavení registru pro úroveň ClearType je individuální uživatelské nastavení, které odpovídá určitému názvu zobrazovacího zařízení:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý zobrazovaný název zařízení pro uživatele `ClearTypeLevel` je definována hodnota DWORD. Následující snímek obrazovky ukazuje nastavení editoru registru pro úroveň ClearType.  
  
 ![Nastavení technologie ClearType v editoru registru.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikace vykreslí text v jednom z obou režimů s technologií ClearType a bez něj. Když se text vykresluje bez technologie ClearType, označuje se jako vykreslování v šedé škále.  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Úroveň gamma  
 Úroveň gamma odkazuje na nelineární vztah mezi hodnotou pixelu a světelností. Nastavení úrovně gamma by mělo odpovídat fyzickým charakteristikám zobrazovacího zařízení; v opačném případě může dojít k narušením vykresleného výstupu. Například test může být příliš velký nebo příliš úzký nebo se může zobrazit Barva olemování na hranách svislých stonků glyfů.  
  
 Úroveň gamma je celočíselná hodnota, která je v rozsahu od 1000 do 2200. Výchozí úroveň je 1900.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Umístění nastavení registru pro úroveň gamma je nastavení místního počítače, které odpovídá určitému názvu zobrazovacího zařízení:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý zobrazovaný název zařízení pro uživatele `GammaLevel` je definována hodnota DWORD. Následující snímek obrazovky ukazuje nastavení editoru registru pro úroveň gamma.  
  
 ![Nastavení úrovně gamma technologie ClearType v editoru registru](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>Pixel – struktura  
 Struktura pixelu popisuje typ pixelů, ze kterého se tvoří zobrazovací zařízení. Struktura pixel je definována jako jeden ze tří typů:  
  
|type|Value|Popis|  
|----------|-----------|-----------------|  
|Kopie|0|Zobrazovací zařízení nemá strukturu pixelů. To znamená, že světlé zdroje pro každou barvu jsou rovnoměrně rozloženy v oblasti pixelů – to se označuje jako vykreslování v šedé škále. Toto je způsob, jakým funguje standardní zobrazovací zařízení. Technologie ClearType se pro vykreslený text nikdy nepoužívá.|  
|RGB|1|Zobrazovací zařízení obsahuje pixely, které se skládají ze tří pruhů v následujícím pořadí: červená, zelená a modrá. Technologie ClearType se aplikuje na vykreslený text.|  
|BGR|2|Zobrazovací zařízení obsahuje pixely, které se skládají ze tří pruhů v následujícím pořadí: modrá, zelená a červená. Technologie ClearType se aplikuje na vykreslený text. Všimněte si, jak je pořadí převráceno z typu RGB.|  
  
 Struktura pixelů odpovídá celočíselné hodnotě, která je v rozsahu od 0 do 2. Výchozí úroveň je 0, což představuje strukturu plochých pixelů.  
  
> [!NOTE]
> Informace o vytváření výčtu zobrazovaných názvů zařízení najdete ve `EnumDisplayDevices` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkci.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Umístění nastavení registru pro strukturu pixelů je nastavení místního počítače, které odpovídá určitému názvu zobrazovacího zařízení:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý zobrazovaný název zařízení pro uživatele `PixelStructure` je definována hodnota DWORD. Následující snímek obrazovky ukazuje nastavení editoru registru pro strukturu pixelů.  
  
 ![Nastavení úrovně gamma technologie ClearType v editoru registru](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>Úroveň kontrastu textu  
 Úroveň kontrastu textu umožňuje upravit vykreslování textu na základě šířky stonků glyfů. Úroveň kontrastu textu je celočíselná hodnota, která je v rozsahu od 0 do 6 – čím větší je celočíselná hodnota, tím širší je kmen. Výchozí úroveň je 1.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Umístění nastavení registru pro úroveň kontrastu textu je individuální uživatelské nastavení, které odpovídá určitému názvu zobrazovacího zařízení:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý zobrazovaný název zařízení pro uživatele `TextContrastLevel` je definována hodnota DWORD. Následující snímek obrazovky ukazuje nastavení editoru registru pro úroveň kontrastu textu.  
  
 ![Nastavení technologie ClearType v editoru registru.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>Viz také:

- [ClearType – přehled](cleartype-overview.md)
- [Antialiasing ClearType](/windows/desktop/gdi/cleartype-antialiasing)
