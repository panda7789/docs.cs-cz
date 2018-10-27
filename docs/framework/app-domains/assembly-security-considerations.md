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
ms.openlocfilehash: 8d83da6e995c35de650c496c5792e55b05dd9095
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50088790"
---
# <a name="assembly-security-considerations"></a>Důležité informace o zabezpečení sestavení
<a name="top"></a> Při sestavování sestavení, můžete zadat sadu oprávnění, která vyžaduje sestavení ke spuštění. Legitimace vychází, zda jsou určitá oprávnění udělit nebo nebyla udělena na sestavení.  
  
 Legitimace se používá dva různé způsoby:  
  
-   Vstupní legitimace se sloučí s legitimací shromážděné zavaděč, chcete-li vytvořit finální sada ověření pro řešení zásady. Metody, které používají tuto sémantiku patří **Assembly.Load**, **Assembly.LoadFrom**, a **Activator.CreateInstance**.  
  
-   Vstupní legitimace se používá beze změny jako výsledná sada ověření pro řešení zásady. Metody, které používají tuto sémantiku patří **Assembly.Load(byte[])** a **AppDomain.DefineDynamicAssembly()**.  
  
 Volitelné oprávnění lze udělit pomocí [zásady zabezpečení](../../../docs/framework/misc/code-access-security-basics.md) nastavit v počítači, ve kterém se spustí sestavení. Pokud chcete svůj kód pro zpracování všechny potenciální výjimky zabezpečení, můžete provést jednu z následujících:  
  
-   Vložte žádost o oprávnění pro všechna oprávnění, musíte mít kód a ještě před zahájením zpracování selhání během načítání, který nastane, pokud nejsou udělena oprávnění.  
  
-   Nepoužívejte žádosti o oprávnění k získání oprávnění váš kód může být nutné, ale být připravena ke zpracování bezpečnostním výjimkám, pokud nejsou udělena oprávnění.  
  
    > [!NOTE]
    >  Zabezpečení je komplexní oblast a můžete vybírat z mnoha různými způsoby. Další informace najdete v tématu [klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md).  
  
 V okamžiku načtení legitimaci sestavení používá jako vstup pro zásady zabezpečení. Zásady zabezpečení se stanoví podle podniku a správce počítače a nastavení zásad pro uživatele a určuje sadu oprávnění udělenou všechen spravovaný kód při spuštění. Zásady zabezpečení je možné navázat vydavatele sestavení (Pokud má podpisový generovaných nástrojem pro podpis), webu a zóny (v Internet Exploreru podmínky) sestavení byl stažen z nebo pro sestavení silným názvem. Například správce počítače můžete vytvořit zásady zabezpečení, které umožňuje veškerý kód stáhnout z webu a podepsány dané softwarová společnost pro přístup k databázi v počítači, ale bez možnosti udělovat přístup k zápisu na disk počítače.  
  
## <a name="strong-named-assemblies-and-signing-tools"></a>Sestavení se silným názvem a nástroje pro podepisování  

 > [!WARNING]
 > Nespoléhejte na silných názvů pro zabezpečení. Poskytují jedinečné identity.

 Sestavení lze podepsat ve dvou různých ale vzájemně doplňují způsoby: pomocí silného názvu nebo s použitím [SignTool.exe (nástroj Sign Tool)](../../../docs/framework/tools/signtool-exe.md). Podepisování sestavení silným názvem přidá veřejný šifrovací klíče do souboru, který obsahuje manifest sestavení. Podepisování se silným názvem pomáhá zkontrolujte jedinečnost názvu, bránit falšování a poskytnout volající některé identity, když je vyřešený odkaz.  
  
 Žádná úroveň vztahu důvěryhodnosti není přidružená silným názvem, díky čemuž je [SignTool.exe (nástroj Sign Tool)](../../../docs/framework/tools/signtool-exe.md) důležité. Dva podpisový nástroje vyžadují, aby vydavatel prokáže svoji identitu autoritu třetí strany a získat certifikát. Tento certifikát bude poté vložen do souboru a můžou používat Správce rozhodnout, zda důvěřovat pravosti kódu.  
  
 Můžete udělit silného názvu a digitální podpis vytvořený pomocí [SignTool.exe (nástroj Sign Tool)](../../../docs/framework/tools/signtool-exe.md) na sestavení, nebo můžete použít buď samostatně. Dva nástroje pro podepisování se můžete přihlásit pouze jeden soubor najednou. Vícesouborové sestavení podepsat soubor, který obsahuje manifest sestavení. Silný název je uložen v souboru, který obsahuje manifest sestavení, ale signatura vytvořena pomocí [SignTool.exe (nástroj Sign Tool)](../../../docs/framework/tools/signtool-exe.md) je uložen v vyhrazené místo v souboru (PE portable executable), který obsahuje manifest sestavení. Podepisování sestavení pomocí [SignTool.exe (nástroj Sign Tool)](../../../docs/framework/tools/signtool-exe.md) lze použít (s nebo bez silného názvu) Pokud již máte důvěryhodnost hierarchie, která závisí na[SignTool.exe (nástroj Sign Tool)](../../../docs/framework/tools/signtool-exe.md) vygeneruje podpisy, nebo když vaše zásady používá pouze část klíče a nekontroluje řetěz certifikátů.  
  
> [!NOTE]
>  Při použití silným názvem a podpisem podpisový nástroj na sestavení, silný název musí být nejprve přiřazena.  
  
 Modul common language runtime také provádí ověření algoritmu hash; manifest sestavení obsahuje seznam všech souborů, které tvoří sestavení, včetně hodnoty hash každého souboru, který existoval, když byla vytvořena v manifestu. Po načtení jednotlivých souborů je z obsahu vytvořena hodnota hash a ta je porovnána s hodnotou hash uloženou v manifestu. Pokud se tyto dvě hodnoty hash neshodují, sestavení se nepodaří načíst.  
  
 Protože silné pojmenovávání a podepisování pomocí [SignTool.exe (nástroj Sign Tool)](../../../docs/framework/tools/signtool-exe.md) zaručit integritu, zásady zabezpečení přístupu kódu můžete založit na tyto dvě formy legitimaci sestavení. Silné názvy a podepisování pomocí [SignTool.exe (nástroj Sign Tool)](../../../docs/framework/tools/signtool-exe.md) zaručit integritu prostřednictvím digitálních podpisů a certifikáty. Všechny uvedené technologie – hodnoty hash ověřování, silné názvy a podepisování pomocí [SignTool.exe (nástroj Sign Tool)](../../../docs/framework/tools/signtool-exe.md)– spolupracují, aby se ujistěte, že sestavení nebyl změněn žádným způsobem.  
  
## <a name="see-also"></a>Viz také  
- [Sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md)  
- [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
- [SignTool.exe (nástroj pro podpis)](../../../docs/framework/tools/signtool-exe.md)
