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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83797ba0934be1c29a3bf9ff37dde430477cfe23
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973010"
---
# <a name="assembly-versioning"></a>Správa verzí sestavení
Všechna verze sestavení, která používají modul CLR (Common Language Runtime), je provedena na úrovni sestavení. Konkrétní verze sestavení a verze závislých sestavení jsou zaznamenány v manifestu sestavení. Výchozí zásady verze modulu runtime jsou aplikace spouštěny pouze s verzemi, které byly vytvořeny a testovány pomocí nástroje, pokud nejsou přepsány explicitními zásadami verze v konfiguračních souborech (konfigurační soubor aplikace, soubor zásad vydavatele a konfigurační soubor správce počítače).  
  
> [!NOTE]
> Správa verzí se provádí pouze v sestaveních se silnými názvy.  
  
 Modul runtime provede několik kroků pro vyřešení požadavku vazby sestavení:  
  
1. Zkontroluje původní odkaz na sestavení a určí verzi sestavení, která se má svázat.  
  
2. Kontroluje všechny použitelné konfigurační soubory pro použití zásad verze.  
  
3. Určuje správné sestavení z původního odkazu na sestavení a veškeré přesměrování zadané v konfiguračních souborech a určuje verzi, která má být svázána s volajícím sestavením.  
  
4. Kontroluje globální mezipaměť sestavení (GAC), základy kódu zadané v konfiguračních souborech a pak kontroluje adresář a podadresáře aplikace pomocí pravidel pro zjišťování, která jsou vysvětlena v tématu [jak modul runtime vyhledává sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Následující ilustrace znázorňuje tyto kroky:  
  
 ![Diagram, který ukazuje kroky v řešení požadavků vazby sestavení](./media/versioning/resolve-assembly-binding-request.gif)
  
 Další informace o konfiguraci aplikací najdete v tématu [Konfigurace](../../../docs/framework/configure-apps/index.md)aplikací. Další informace o zásadách vázání najdete v tématu [jak modul runtime vyhledává sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md).  
  
## <a name="version-information"></a>Informace o verzi  
 Každé sestavení má dva různé způsoby, jak vyjádřit informace o verzi:  
  
- Číslo verze sestavení, které spolu s názvem sestavení a informacemi o jazykové verzi, je součástí identity sestavení. Toto číslo používá modul runtime k vyhodnocování zásad verze a hraje v procesu rozlišení typu za běhu klíčovou část.  
  
- Informační verze, což je řetězec, který představuje další informace o verzi obsažené pouze pro informativní účely.  
  
### <a name="assembly-version-number"></a>Číslo verze sestavení  
 Každé sestavení má v rámci své identity číslo verze. V takovém případě se dvě sestavení, která se liší číslem verze, považují za modul runtime za zcela odlišná sestavení. Toto číslo verze je fyzicky reprezentované jako řetězec o čtyřech částech v následujícím formátu:  
  
 \<> *hlavní verze*. *vedlejší verze >.* \< *číslo buildu >.* \< \< *Revize*>  
  
 Například verze 1.5.1254.0 označuje 1 jako hlavní verzi, 5 jako dílčí verzi, 1254 jako číslo sestavení a 0 jako číslo revize.  
  
 Číslo verze je uloženo v manifestu sestavení spolu s dalšími informacemi o identitě, včetně názvu sestavení a veřejného klíče, a také informace o relacích a identitách jiných sestavení připojených k aplikaci.  
  
 Při sestavování sestavení Nástroj pro vývoj zaznamenává informace o závislostech pro každé sestavení, na které je odkazováno v manifestu sestavení. Modul runtime používá tato čísla verzí ve spojení s konfiguračními informacemi nastavenými správcem, aplikací nebo vydavatelem k načtení správné verze odkazovaného sestavení.  
  
 Modul runtime rozlišuje běžné a silně pojmenované sestavení pro účely správy verzí. Kontrola verze se vyskytuje pouze u sestavení se silným názvem.  
  
 Informace o zadávání zásad vázání verzí najdete v tématu [Konfigurace aplikací](../../../docs/framework/configure-apps/index.md). Informace o tom, jak modul runtime používá informace o verzi k nalezení konkrétního sestavení, naleznete v tématu [jak modul runtime vyhledává sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md).  
  
### <a name="assembly-informational-version"></a>Informační verze sestavení  
 Informační verze je řetězec, který připojuje informace o dalších verzích k sestavení pouze pro informativní účely. Tyto informace se nepoužívají v době běhu. Textová informační verze odpovídá marketingové dokumentaci produktu, balení nebo názvu produktu a není používána modulem runtime. Informační verze může být například "modul common language runtime verze 1,0" nebo "NET Control SP 2". Na kartě verze v dialogovém okně Vlastnosti souboru v systému Microsoft Windows se tyto informace zobrazí v položce "verze produktu".  
  
> [!NOTE]
> I když můžete zadat libovolný text, zobrazí se při kompilaci zpráva upozornění, pokud řetězec není ve formátu používaném číslem verze sestavení, nebo pokud je v tomto formátu, ale obsahuje zástupné znaky. Toto upozornění je neškodné.  
  
 Informační verze je reprezentovaná pomocí vlastního atributu <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>. Další informace o atributu informační verze naleznete v tématu [set Assembly Attributes](set-attributes.md).  
  
## <a name="see-also"></a>Viz také:

- [Způsob, jakým modul runtime vyhledává sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurace aplikací](../../framework/configure-apps/index.md)
- [Nastavit atributy sestavení](set-attributes.md)
- [Sestavení v .NET](index.md)
