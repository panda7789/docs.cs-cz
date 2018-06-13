---
title: Důležité informace o zabezpečení sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], security
- signcodes
- names [.NET Framework], assemblies
- strong-named assemblies, security considerations
- signing assemblies
- assemblies [.NET Framework], signing
- granting permissions, assemblies
- assemblies [.NET Framework], strong-named
- names [.NET Framework], strong names
- permissions [.NET Framework], assemblies
- security [.NET Framework], assemblies
- integrity with assemblies
ms.assetid: 1b5439c1-f3d5-4529-bd69-01814703d067
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4f791ea339c9188ac8fada525611fc68821351d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743417"
---
# <a name="assembly-security-considerations"></a>Důležité informace o zabezpečení sestavení
<a name="top"></a> Při vytváření sestavení, můžete sadu oprávnění, která sestavení vyžaduje ke spuštění. Zda jsou některá oprávnění udělit nebo nejsou udělena sestavení je založena na důkaz.  
  
 Existují dva způsoby distinct, důkaz se používá:  
  
-   Vstupní důkaz je sloučen s důkaz shromáždit zavaděčem vytvořit závěrečnou sadu důkaz slouží k rozlišení zásad. Metody, které používají tuto sémantiku patří **Assembly.Load**, **Assembly.LoadFrom**, a **Activator.CreateInstance**.  
  
-   Vstupní důkaz se používá jako závěrečné sady důkaz slouží k rozlišení zásad v nezměněném stavu. Metody, které používají tuto sémantiku patří **Assembly.Load(byte[])** a **AppDomain.DefineDynamicAssembly()**.  
  
 Volitelné oprávnění můžete udělit pomocí [zásady zabezpečení](../../../docs/framework/misc/code-access-security-basics.md) nastavit v počítači, kde se spustí sestavení. Pokud chcete, aby váš kód zpracovávat všechny potenciální výjimky zabezpečení, můžete provést jednu z těchto možností:  
  
-   Vložte žádost oprávnění pro všechna oprávnění kódu musí mít a zpracovat předem čas načítání selhání, který nastane, pokud nejsou udělena oprávnění.  
  
-   Nepoužívejte žádost o oprávnění k získání oprávnění kódu může být nutné, ale připravte se na zpracování výjimek zabezpečení, pokud nejsou udělena oprávnění.  
  
    > [!NOTE]
    >  Zabezpečení je komplexní oblasti a mají mnoho možností pro vybírat. Další informace najdete v tématu [klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md).  
  
 V okamžiku načtení sestavení důkaz slouží jako vstup pro zásady zabezpečení. Zásady zabezpečení je vytvořena podle podniku a správce počítače a nastavení zásad pro uživatele a určuje sadu oprávnění udělenou po provedení všech spravovaného kódu. Zásady zabezpečení lze navázat pro vydavatele sestavení (Pokud má podpisový generovaných nástrojem podpis), sestavení pro webový server a zónu (v Internet Exploreru podmínky) byl stažen z nebo pro silný název sestavení. Správce počítače můžete například vytvořit zásady zabezpečení, která umožňuje všechny kód stáhnout z webu a podepsaný daný software společnosti pro přístup k databázi v počítači, ale neposkytuje přístup k zápisu na disku.  
  
## <a name="strong-named-assemblies-and-signing-tools"></a>Sestavení se silným názvem a podepisování nástroje  
 Sestavení můžete přihlásit dva různé ale vzájemně doplňují způsoby: silným názvem nebo pomocí [SignTool.exe (nástroj pro podpis)](../../../docs/framework/tools/signtool-exe.md). Podepisování sestavení se silným názvem přidá veřejný šifrovací klíče do souboru, který obsahuje manifest sestavení. Podpis silného názvu pomáhá ověřit jedinečnost názvu, zabránit falšování a poskytnout volající některé identity když odkaz je vyřešený.  
  
 Ale žádná úroveň důvěryhodnosti souvisí se silným názvem, díky čemuž [SignTool.exe (nástroj pro podpis)](../../../docs/framework/tools/signtool-exe.md) důležité. Tyto podepisovací nástroje vyžadují vydavatele k prokázání své identity autority třetích stran a získat certifikát. Tento certifikát se pak vloží v souboru a můžete použít správce můžete rozhodnout, jestli důvěřovat pravosti kódu.  
  
 Můžete udělit silným názvem i digitální podpis vytvořený [SignTool.exe (nástroj pro podpis)](../../../docs/framework/tools/signtool-exe.md) k sestavení, nebo můžete použít buď samostatně. Tyto podepisovací nástroje můžete přihlásit pouze jeden soubor současně; pro vícesouborového sestavení podepsat soubor, který obsahuje manifest sestavení. Silné jméno je uložené v souboru, který obsahuje manifest sestavení, ale podpis vytvořený [SignTool.exe (nástroj pro podpis)](../../../docs/framework/tools/signtool-exe.md) je uložen v vyhrazené sektoru přenosné spustitelného souboru (PE), který obsahuje manifest sestavení. Podepisování sestavení pomocí [SignTool.exe (nástroj pro podpis)](../../../docs/framework/tools/signtool-exe.md) lze (s nebo bez silný název) Pokud již máte hierarchie důvěryhodnosti, které jsou závislé na[SignTool.exe (nástroj pro podpis)](../../../docs/framework/tools/signtool-exe.md) generované podpisu nebo pokud vaše zásady používá jenom část klíče a nekontroluje řetěz certifikátů.  
  
> [!NOTE]
>  Při použití silným názvem a podepisování podpis nástroj na sestavení, musí být silný název nejprve přiřazen.  
  
 Modul common language runtime také provede ověření algoritmu hash; manifest sestavení obsahuje seznam všech souborů, které tvoří sestavení, včetně hodnota hash každý soubor, který existoval, když byl vytvořený v manifestu. Po načtení jednotlivých souborů je z obsahu vytvořena hodnota hash a ta je porovnána s hodnotou hash uloženou v manifestu. Pokud se tyto dvě hodnoty hash neshodují, sestavení se nepodaří načíst.  
  
 Protože silné pojmenování a podepisování pomocí [SignTool.exe (nástroj pro podpis)](../../../docs/framework/tools/signtool-exe.md) zaručí integritu, zásady zabezpečení přístupu kódu můžete založit na tyto dvě formy důkaz sestavení. Silné názvy a podepisování pomocí [SignTool.exe (nástroj pro podpis)](../../../docs/framework/tools/signtool-exe.md) zaručí integritu prostřednictvím digitálních podpisů a certifikátů. Všechny zmíněné technologie – hash ověření, silné názvy a podepisování pomocí [SignTool.exe (nástroj pro podpis)](../../../docs/framework/tools/signtool-exe.md)– spolupracují, aby se ujistěte, že sestavení nezměnil žádným způsobem.  
  
## <a name="see-also"></a>Viz také  
 [Sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md)  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [SignTool.exe (nástroj pro podpis)](../../../docs/framework/tools/signtool-exe.md)
