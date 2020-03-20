---
title: Nastavení registru ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: bedd99fcf9b4ca1d10b4c24d7cff9de320e6fd12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186166"
---
# <a name="cleartype-registry-settings"></a>Nastavení registru ClearType
Toto téma obsahuje přehled nastavení registru Microsoft ClearType, které používají aplikace WPF.  

<a name="overview"></a>
## <a name="technology-overview"></a>Přehled technologií  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Aplikace, které vykreslují text do zobrazovacího zařízení, používají funkce ClearType k lepšímu čtení. ClearType je softwarová technologie vyvinutá společností Microsoft, která zlepšuje čitelnost textu na stávajících LCD (displeje z tekutých krystalů), jako jsou obrazovky notebooků, obrazovky kapesních počítačů a ploché monitory. Funkce ClearType funguje tak, že přistupuje k jednotlivým prvkům svislého barevného proužku v každém pixelu obrazovky LCD. Další informace o příkazu ClearType naleznete v [tématu Přehled jazyka ClearType](cleartype-overview.md).  
  
 Text, který je vykreslen pomocí příkazu ClearType, se může při zobrazení na různých zobrazovacích zařízeních výrazně lišit. Například malý počet monitorů implementuje prvky barevného proužku v modrém, zeleném, červeném pořadí spíše než v běžnějším pořadí červené, zelené, modré (RGB).  
  
 Text, který je vykreslen pomocí funkce ClearType, se může také výrazně lišit při zobrazení jednotlivci s různou úrovní barevné citlivosti. Někteří jedinci mohou detekovat mírné rozdíly v barvě lépe než ostatní.  
  
 V každém z těchto případů cleartype funkce je třeba upravit tak, aby poskytovaly nejlepší čtení pro každého jednotlivce.  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>Nastavení registru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]určuje čtyři nastavení registru pro řízení funkcí cleartype:  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|Úroveň ClearType|Popisuje úroveň čistoty barev ClearType.|  
|Úroveň gama|Popisuje úroveň barevné komponenty obrazových bodů pro zobrazovací zařízení.|  
|Struktura pixelů|Popisuje uspořádání pixelů pro zobrazovací zařízení.|  
|Úroveň kontrastu textu|Popisuje úroveň kontrastu zobrazeného textu.|  
  
 K těmto nastavením lze přistupovat pomocí externího konfiguračního nástroje, který ví, jak odkazovat na identifikované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavení registru ClearType. Tato nastavení lze také vytvořit nebo upravit přístupem k hodnotám přímo pomocí Editoru registru systému Windows.  
  
 Pokud [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] není nastaveno nastavení registru ClearType (což [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je výchozí stav), aplikace se dotazuje na informace o systémových parametrech systému Windows pro nastavení vyhlazení písma.  
  
> [!NOTE]
> Informace o výčtu názvů zobrazovacích `SystemParametersInfo`zařízení naleznete v tématu Win32 funkce.  
  
<a name="ClearType_level"></a>
## <a name="cleartype-level"></a>Úroveň cleartype  
 Úroveň ClearType umožňuje upravit vykreslování textu na základě barevné citlivosti a vnímání jednotlivce. Pro některé jednotlivce vykreslování textu, který používá ClearType na nejvyšší úrovni neposkytuje nejlepší čtení.  
  
 Úroveň ClearType je celá hodnota, která se pohybuje od 0 do 100. Výchozí úroveň je 100, což znamená, že ClearType využívá maximální schopnost prvků barevného proužku zobrazovacího zařízení. Úroveň ClearType 0 však vykreslí text jako šedou stupnici. Nastavením úrovně ClearType někde mezi 0 a 100 můžete vytvořit mezilehlou úroveň, která je vhodná pro barevnou citlivost jednotlivce.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Umístění nastavení registru pro úroveň ClearType je individuální uživatelské nastavení, které odpovídá konkrétnímu názvu zobrazovacího zařízení:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý název zobrazovacího zařízení `ClearTypeLevel` pro uživatele je definována hodnota DWORD. Následující snímek obrazovky ukazuje nastavení Editoru registru pro úroveň ClearType.  
  
 ![Nastavení ClearType v Editoru registru.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikace vykreslují text v jednom ze dvou režimů, s a bez ClearType. Pokud je text vykreslen bez příkazu ClearType, označuje se jako vykreslování ve stupních šedi.  
  
<a name="gamma_level"></a>
## <a name="gamma-level"></a>Úroveň gama  
 Úroveň gama odkazuje na nelineární vztah mezi hodnotou obrazového bodu a světlostí. Nastavení úrovně gama by mělo odpovídat fyzikálním vlastnostem zobrazovacího zařízení; v opačném případě může dojít k deformaci vykresleného výstupu. Text může být například příliš široký nebo příliš úzký nebo se na okrajích svislých stonků glyfů mohou objevit barevné okraje.  
  
 Úroveň gama je celá hodnota, která se pohybuje od 1000 do 2200. Výchozí úroveň je 1900.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Umístění nastavení registru pro úroveň gama je nastavení místního počítače, které odpovídá určitému názvu zobrazovacího zařízení:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý název zobrazovacího zařízení `GammaLevel` pro uživatele je definována hodnota DWORD. Následující snímek obrazovky ukazuje nastavení Editoru registru pro úroveň gama.  
  
 ![Nastavení úrovně gama clearType v Editoru registru](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>
## <a name="pixel-structure"></a>Struktura pixelů  
 Struktura obrazových bodů popisuje typ pixelů, které tvoří zobrazovací zařízení. Struktura obrazových bodů je definována jako jeden ze tří typů:  
  
|Typ|Hodnota|Popis|  
|----------|-----------|-----------------|  
|Ploché|0|Zobrazovací zařízení nemá žádnou strukturu pixelů. To znamená, že světelné zdroje pro každou barvu jsou rozloženy rovnoměrně v oblasti obrazových bodů – označuje se jako vykreslování ve stupních šedi. Takto funguje standardní zobrazovací zařízení. Příkaz ClearType se nikdy nepoužije na vykreslený text.|  
|RGB|1|Zobrazovací zařízení má pixely, které se skládají ze tří pruhů v následujícím pořadí: červená, zelená a modrá. Na vykreslený text se použije příkaz ClearType.|  
|Bgr|2|Zobrazovací zařízení má pixely, které se skládají ze tří pruhů v následujícím pořadí: modré, zelené a červené. Na vykreslený text se použije příkaz ClearType. Všimněte si, jak je pořadí obráceno z typu RGB.|  
  
 Struktura obrazových bodů odpovídá celé hodnotě, která se pohybuje od 0 do 2. Výchozí úroveň je 0, což představuje strukturu plochých obrazových bodů.  
  
> [!NOTE]
> Informace o výčtu názvů zobrazovacích `EnumDisplayDevices`zařízení naleznete v tématu Win32 funkce.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Umístění nastavení registru pro strukturu obrazových bodů je nastavení místního počítače, které odpovídá konkrétnímu názvu zobrazovacího zařízení:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý název zobrazovacího zařízení `PixelStructure` pro uživatele je definována hodnota DWORD. Následující snímek obrazovky ukazuje nastavení Editoru registru pro strukturu pixelů.  
  
 ![Nastavení úrovně gama clearType v Editoru registru](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>
## <a name="text-contrast-level"></a>Úroveň kontrastu textu  
 Úroveň kontrastu textu umožňuje upravit vykreslování textu na základě šířky stonku glyfů. Úroveň kontrastu textu je celá hodnota, která se pohybuje od 0 do 6 – čím větší je celá hodnota, tím širší je stopka. Výchozí úroveň je 1.  
  
### <a name="registry-setting"></a>Nastavení registru  
 Umístění nastavení registru pro úroveň kontrastu textu je individuální uživatelské nastavení, které odpovídá určitému názvu zobrazovacího zařízení:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pro každý název zobrazovacího zařízení `TextContrastLevel` pro uživatele je definována hodnota DWORD. Následující snímek obrazovky ukazuje nastavení Editoru registru pro úroveň kontrastu textu.  
  
 ![Nastavení ClearType v Editoru registru.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>Viz také

- [ClearType – přehled](cleartype-overview.md)
- [Vyhlazení cleartype](/windows/desktop/gdi/cleartype-antialiasing)
