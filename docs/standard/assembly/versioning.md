---
title: Správa verzí sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
ms.openlocfilehash: bbb3dae2ce66c93d05a2a1c0f7e426901fa7b2e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140175"
---
# <a name="assembly-versioning"></a>Správa verzí sestavení

Všechna správa verzí sestavení, které používají za běhu společného jazyka, se provádějí na úrovni sestavení. Konkrétní verze sestavení a verze závislých sestavení jsou zaznamenány v manifestu sestavení. Výchozí zásadou verze pro běhový čas je, že aplikace běží pouze s verzemi, které byly vytvořeny a testovány, pokud nejsou přepsány explicitními zásadami verze v konfiguračních souborech (konfigurační soubor aplikace, soubor zásad vydavatele a konfiguračního souboru správce počítače).  
  
> [!NOTE]
> Správa verzí se provádí pouze na sestaveních se silnými názvy.  
  
Runtime provede několik kroků k vyřešení požadavku na vazbu sestavení:  
  
1. Zkontroluje původní odkaz na sestavení a určí verzi sestavení, která má být vázána.  
  
2. Zkontroluje všechny příslušné konfigurační soubory, aby se použily zásady verze.  
  
3. Určuje správné sestavení z původního odkazu sestavení a jakékoli přesměrování zadané v konfiguračních souborech a určuje verzi, která by měla být vázána na volající sestavení.  
  
4. Zkontroluje globální mezipaměť sestavení, základy kódu zadané v konfiguračních souborech a potom zkontroluje adresář a podadresáře aplikace pomocí pravidel zjišťování vysvětlených v části [Jak runtime vyhledá sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md).  
  
Následující obrázek znázorňuje tyto kroky:  
  
![Diagram, který ukazuje kroky v řešení požadavku na vazbu sestavení.](./media/versioning/resolve-assembly-binding-request.gif)
  
Další informace o konfiguraci aplikací naleznete v [tématu Konfigurace aplikací](../../framework/configure-apps/index.md). Další informace o zásadách vazby naleznete [v tématu Jak runtime vyhledá sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md).  
  
## <a name="version-information"></a>Informace o verzi  

Každé sestavení má dva odlišné způsoby vyjádření informací o verzi:  
  
- Číslo verze sestavení, které je spolu s názvem sestavení a informacemi o jazykové verzi součástí identity sestavení. Toto číslo používá za běhu k vynucení zásad verze a hraje klíčovou roli v procesu rozlišení typu za běhu.  
  
- Informační verze, což je řetězec, který představuje další informace o verzi zahrnuty pouze pro informační účely.  
  
### <a name="assembly-version-number"></a>Číslo verze sestavení  

Každé sestavení má číslo verze jako součást své identity. Jako takové dvě sestavení, které se liší podle čísla verze jsou považovány za za zcela odlišné sestavení. Toto číslo verze je fyzicky reprezentováno jako čtyřdílný řetězec v následujícím formátu:  
  
\<*hlavní verze*>. \< *dílčí verze*>. \< *číslo sestavení*>. \< *revize*>  
  
Například verze 1.5.1254.0 označuje 1 jako hlavní verzi, 5 jako dílčí verzi, 1254 jako číslo sestavení a 0 jako číslo revize.  
  
Číslo verze je uloženo v manifestu sestavení spolu s dalšími informacemi o identitě, včetně názvu sestavení a veřejného klíče, stejně jako informace o vztazích a identitách jiných sestavení spojených s aplikací.  
  
Při sestavení sestavení nástroj pro vývoj zaznamenává informace o závislostech pro každé sestavení, na které se odkazuje v manifestu sestavení. Runtime používá tato čísla verzí ve spojení s informacemi o konfiguraci nastavenými správcem, aplikací nebo vydavatelem k načtení správné verze odkazovaného sestavení.  
  
Runtime rozlišuje mezi pravidelnými a silnými pojmenovanými sestaveními pro účely správy verzí. Kontrola verze probíhá pouze u sestavení se silným názvem.  
  
Informace o určení zásad vazby verzí naleznete v [tématu Konfigurace aplikací](../../framework/configure-apps/index.md). Informace o tom, jak runtime používá informace o verzi k vyhledání konkrétního sestavení, naleznete [v tématu Jak runtime vyhledá sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md).  
  
### <a name="assembly-informational-version"></a>Informační verze sestavení  

Informační verze je řetězec, který připojuje další informace o verzi sestavení pouze pro informační účely; Tyto informace nejsou používány za běhu. Textová informační verze odpovídá marketingové literatuře, obalu nebo názvu produktu produktu a není používána za běhu. Informační verze může být například "Common Language Runtime verze 1.0" nebo "NET Control SP 2". Na kartě Verze dialogového okna Vlastnosti souboru v systému Microsoft Windows se tyto informace zobrazí v položce Verze produktu.  
  
> [!NOTE]
> Přestože můžete zadat libovolný text, zobrazí se v kompilaci varovná zpráva, pokud řetězec není ve formátu používaném číslem verze sestavení nebo pokud je v tomto formátu, ale obsahuje zástupné znaky. Toto upozornění je neškodné.  
  
Informační verze je reprezentována <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>pomocí vlastního atributu . Další informace o atributu informační verze naleznete v tématu [Set assembly attributes](set-attributes.md).  
  
## <a name="see-also"></a>Viz také

- [Jak runtime vyhledá sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurace aplikací](../../framework/configure-apps/index.md)
- [Nastavování atributů sestavení](set-attributes.md)
- [Sestavení v .NET](index.md)
