---
title: Správa verzí sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87fb99ee8379a14a4a1d272a6eabb7fa8413bf64
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724067"
---
# <a name="assembly-versioning"></a>Správa verzí sestavení
Všechny verze sestavení, které používají modul common language runtime se provádí na úrovni sestavení. Konkrétní verzi sestavení a verze závislých sestavení jsou zaznamenány v manifestu sestavení. Výchozí zásada verze modulu runtime je, že aplikace spuštěny pouze verze by byly vytvořené a testovány, pokud není přepsán explicitní verze zásad v konfiguračních souborech (konfigurační soubor aplikace, soubor zásad vydavatele a Správce konfigurační soubor počítače).  
  
> [!NOTE]
>  Správa verzí se provádí pouze na sestavení se silnými názvy.  
  
 Modul runtime provádí několik kroků pro řešení požadavků sestavení na vazby:  
  
1.  Ověří původní odkaz na sestavení pro určení verze sestavení, které má být vázána.  
  
2.  Kontroly všech příslušných konfiguračních souborů pro použití zásad správy verzí.  
  
3.  Určuje správné sestavení z původní odkaz na sestavení a všechny přesměrování zadaný v konfiguračních souborech a určuje verze, která by měla být vázána na volajícího sestavení.  
  
4.  Zkontroluje globální mezipaměti sestavení, základů kódu v konfiguračních souborech a pak kontroluje aplikace adresáře a podadresáře pomocí pravidel zjišťování je vysvětleno v [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Následující obrázek znázorňuje tyto kroky.  
  
 ![.Assembly extern myAssembly](../../../docs/framework/app-domains/media/versioningover.gif "versioningover")  
Řešení požadavků sestavení na vazby  
  
 Další informace o konfiguraci aplikací najdete v tématu [konfigurace aplikace](../../../docs/framework/configure-apps/index.md). Další informace o vazbě zásady, najdete v části [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
## <a name="version-information"></a>Informace o verzi  
 Každé sestavení má dva různé způsoby vyjádření informace o verzi:  
  
-   Číslo verze sestavení, které spolu s informace o sestavení název a jazykové verze je součástí identity sestavení. Toto číslo modul runtime používá k vynucení zásad správy verzí a hrají klíčovou součástí v procesu překladu, který typ v době běhu.  
  
-   Informační verze, což je řetězec, který představuje další informace o verzi zahrnuty pouze k informačním účelům.  
  
### <a name="assembly-version-number"></a>Číslo verze sestavení  
 Každé sestavení má číslo verze jako součást jeho identitu. V důsledku toho dvě sestavení, které se liší podle čísla verze jsou považovány za tímto modulem úplně odlišnému sestavení. Toto číslo verze je fyzicky reprezentována jako řetězec sestávající ze čtyř částí v následujícím formátu:  
  
 \<*hlavní verze*>.\< *podverze*>.\< *číslo sestavení*>.\< *revize*>  
  
 Verze 1.5.1254.0 například označuje jako hlavní verze 5 jako vedlejší verze 1, 1254 jako číslo sestavení a 0 jako číslo revize.  
  
 Číslo verze je uloženo v manifestu sestavení spolu s dalšími informacemi o identitě, včetně názvu sestavení a veřejný klíč, stejně jako informace o relacích a identit jiných sestavení spojených s aplikací.  
  
 Pokud sestavení vytvořené, vývojové nástroje záznamy informace o závislostech pro každé sestavení, která je popsána v manifestu sestavení. Modul runtime používá tato čísla verze ve spojení s informace o konfiguraci nastavení správce nebo aplikace, vydavatel, načtení správná verze odkazovaného sestavení.  
  
 Modul runtime rozlišuje mezi pravidelné a silným názvem sestavení pro účely správy verzí. Kontrola verze dochází jenom u sestavení se silným názvem.  
  
 Informace o určení verze vazby zásad najdete v tématu [konfigurace aplikace](../../../docs/framework/configure-apps/index.md). Informace o tom, jak modul runtime používá k vyhledání konkrétního sestavení informace o verzi najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
### <a name="assembly-informational-version"></a>Informační verze sestavení  
 Informační verze je řetězec, který připojí další informace o verzi sestavení; pouze k informačním účelům Tyto informace se používají v době běhu. Informační verze založený na textu odpovídá produktu marketingu dokumentace, balení nebo název produktu a nepoužívá modulem runtime. Informační verze může být například "Common Language Runtime verze 1.0" nebo "NET řízení SP 2". Na kartě verze dialogové okno Vlastnosti souboru v Microsoft Windows tyto informace se zobrazí v položce "Verze produktu".  
  
> [!NOTE]
>  I když můžete zadat libovolný text, upozornění se zobrazí při kompilaci, pokud řetězec není ve formátu používá číslo verze sestavení, nebo pokud je v tomto formátu, ale obsahuje zástupné znaky. Toto upozornění je neškodný.  
  
 Informační verze je reprezentována pomocí vlastního atributu <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>. Další informace o atributu informační verze najdete v tématu [nastavení atributů sestavení](../../../docs/framework/app-domains/set-assembly-attributes.md).  
  
## <a name="see-also"></a>Viz také:
- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurace aplikací](../../../docs/framework/configure-apps/index.md)
- [Nastavování atributů sestavení](../../../docs/framework/app-domains/set-assembly-attributes.md)
- [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
