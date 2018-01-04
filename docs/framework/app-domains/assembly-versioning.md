---
title: "Správa verzí sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 327ef282c23fc02791eb7c531fd1ae25c6700fd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-versioning"></a>Správa verzí sestavení
Všechny verze sestavení, které používají modul common language runtime se provádí na úrovni sestavení. Konkrétní verze sestavení a verze závislé sestavení jsou popsané v manifestu sestavení. Výchozí zásada verze pro modul runtime je, že aplikace spouštět pouze s verzemi, které by byly vytvořené a testovány, není-li přepsat zásady explicitní verze v konfiguračních souborech (konfigurační soubor aplikace, soubor zásad vydavatele a Správce konfigurace souboru počítače).  
  
> [!NOTE]
>  Správa verzí se provádí pouze na sestavení se silnými názvy.  
  
 Modul runtime provede několik postup řešení požadavků sestavení na vazby:  
  
1.  Kontroluje původní odkaz sestavení zjistíte verzi sestavení, které má být vázána.  
  
2.  Kontroluje všechny vhodné konfigurační soubory pro použití zásad správy verzí.  
  
3.  Určuje správné sestavení z původní odkaz sestavení a žádné přesměrování zadaný v konfiguračních souborech a určuje verzi, která by měla být vázána na volajícího sestavení.  
  
4.  Kontroluje globální mezipaměti sestavení, základy kódu v konfigurační soubory a pak kontroluje adresář aplikace a podadresáře pomocí pravidel zjišťování podrobně [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Následující obrázek znázorňuje tyto kroky.  
  
 ![.Assembly extern myAssembly](../../../docs/framework/app-domains/media/versioningover.gif "versioningover")  
Řešení požadavků sestavení na vazby  
  
 Další informace o konfiguraci aplikací najdete v tématu [konfigurace aplikace](../../../docs/framework/configure-apps/index.md). Další informace o zásadách vazby najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
## <a name="version-information"></a>Informace o verzi  
 Každé sestavení má dva odlišné způsoby vyjádření informace o verzi:  
  
-   Číslo verze sestavení, které společně s informace o sestavení název a jazykovou verzi je součástí identity sestavení. Toto číslo se používá modulem runtime k vynucení zásad správy verzí a hraje část klíče v procesu překladu, který typ za běhu.  
  
-   Informační verzi, která je řetězec, který představuje další informace o verzi zahrnuty pouze pro informační účely.  
  
### <a name="assembly-version-number"></a>Číslo verze sestavení  
 Každé sestavení má číslo verze jako součást svou identitu. Jako takový dvou sestavení, které se liší podle čísla verze jsou považovány za modulem runtime úplně jiné sestavení. Toto číslo verze je fyzicky reprezentována jako řetězec sestávající ze čtyř částí v následujícím formátu:  
  
 \<*hlavní verze*>.\< *podverze*>.\< *číslo sestavení*>.\< *revize*>  
  
 Například verze 1.5.1254.0 označuje 1 jako hlavní verze 5 jako podverzi, 1254 jako číslo sestavení a 0 jako číslo revize.  
  
 Číslo verze je uložené v manifestu sestavení společně s dalšími informacemi o identitě včetně na název sestavení a veřejný klíč, a také informace o relacích a identitách jiných sestavení spojených s aplikací.  
  
 Pokud sestavení vytvořené, vývoj nástroj zaznamenává informace o závislostech pro každé sestavení, který se odkazuje v manifestu sestavení. Modul runtime používá tato čísla verze ve spojení s informace o konfiguraci, která nastavuje správce, aplikace nebo vydavatel, k načtení správné verze odkazovaného sestavení.  
  
 Modul runtime rozlišuje mezi obyčejnými a silným názvem sestavení pro účely správy verzí. Kontrola verze dochází pouze s sestavení se silným názvem.  
  
 Informace o zadávání verze vazby zásady najdete v tématu [konfigurace aplikace](../../../docs/framework/configure-apps/index.md). Informace o tom, jak modul runtime používá informace o verzi k vyhledání konkrétního sestavení najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
### <a name="assembly-informational-version"></a>Informační verze sestavení  
 Informační verze je řetězec, který se připojuje k sestavení Další informace o verzi pro informační účely pouze; Tyto informace se nepoužívá v době běhu. Informační verze založený na textu odpovídá produktu marketingové dokumentace, balení nebo název produktu a nepoužívá modulem runtime. Informační verze může být například "Common Language Runtime verze 1.0" nebo "NET řízení SP 2". Na kartě verze v dialogovém okně vlastností souboru v systému Windows tato informace se zobrazí v položce "Verzí produktu".  
  
> [!NOTE]
>  I když můžete zadat libovolný text, upozornění se zobrazí při kompilaci, pokud řetězec není ve formátu používá číslo verze sestavení, nebo pokud je v tomto formátu, ale obsahuje zástupné znaky. Toto upozornění je neškodné.  
  
 Informační verze je reprezentována pomocí vlastního atributu <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>. Další informace o atributu informační verze najdete v tématu [nastavení atributů sestavení](../../../docs/framework/app-domains/set-assembly-attributes.md).  
  
## <a name="see-also"></a>Viz také  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Konfigurace aplikací](../../../docs/framework/configure-apps/index.md)  
 [Nastavování atributů sestavení](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
