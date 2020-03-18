---
title: Důležité informace o zabezpečení sestavení
ms.date: 08/20/2019
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
ms.openlocfilehash: 77c9f9131b556e0b8fa639cd723bf1ca8cd6602e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73972311"
---
# <a name="assembly-security-considerations"></a>Důležité informace o zabezpečení sestavení
Při vytváření sestavení můžete zadat sadu oprávnění, která sestavení vyžaduje ke spuštění. Zda jsou udělena určitá oprávnění nebo nejsou udělena sestavení, je založeno na důkazech.  
  
 Existují dva odlišné způsoby, jak se používá důkaz:  
  
- Vstupní důkazy jsou sloučeny s důkazy shromážděnými zavaděčem k vytvoření konečné sady důkazů použitých pro řešení zásad. Metody, které používají tuto sémantickou patří **Assembly.Load**, **Assembly.LoadFrom**a **Activator.CreateInstance**.  
  
- Vstupní důkazy se používají v nezměněné podobě jako konečný soubor důkazů použitých pro řešení zásad. Metody, které používají tuto sémantickou patří **Assembly.Load(byte[])** a **AppDomain.DefineDynamicAssembly()**.  
  
  Volitelná oprávnění mohou být udělena [zásadami zabezpečení](../../framework/misc/code-access-security-basics.md) nastavenými v počítači, ve kterém bude sestavení spuštěno. Pokud chcete, aby váš kód zpracovat všechny potenciální výjimky zabezpečení, můžete provést jednu z následujících akcí:  
  
- Vložte žádost o oprávnění pro všechna oprávnění, která musí mít váš kód, a zvládněte předem selhání doby načítání, ke kterému dochází, pokud oprávnění nejsou udělena.  
  
- Nepoužívejte žádost o oprávnění k získání oprávnění, která může váš kód potřebovat, ale buďte připraveni na zpracování výjimek zabezpečení, pokud oprávnění nejsou udělena.  
  
  > [!NOTE]
  > Zabezpečení je složitá oblast a máte mnoho možností, ze kterých si můžete vybrat. Další informace naleznete [v tématu Key Security Concepts](../../standard/security/key-security-concepts.md).  
  
 V době načítání důkazy sestavení se používá jako vstup do zásady zabezpečení. Zásady zabezpečení jsou vytvořeny podnikem a správcem počítače a také nastavením zásad uživatele a určují sadu oprávnění, která jsou udělena všem spravovaným kódům při spuštění. Zásady zabezpečení mohou být vytvořeny pro vydavatele sestavení (pokud má podpisový nástroj generovaný podpis), pro web a zónu (v podmínkách aplikace Internet Explorer) bylo sestavení staženo z nebo pro silný název sestavení. Správce počítače může například vytvořit zásady zabezpečení, které umožní všem usměrňovaným kódům staženým z webu a podepsaným danou softwarovou společností přístup k databázi v počítači, ale neudělí přístup k zápisu na disk počítače.  
  
## <a name="strong-named-assemblies-and-signing-tools"></a>Sestavení se silným názvem a nástroje pro podepisování  

 > [!WARNING]
 > Nespoléhejte se na silné názvy pro zabezpečení. Poskytují pouze jedinečnou identitu.

 Sestavení můžete podepsat dvěma různými, ale doplňkovými způsoby: silným názvem nebo pomocí [nástroje SignTool.exe (Sign Tool Tool).](../../framework/tools/signtool-exe.md) Podepisování sestavení se silným názvem přidá šifrování veřejného klíče do souboru obsahujícího manifest sestavení. Podpis silného názvu pomáhá ověřit jedinečnost názvu, zabránit falšování názvů a poskytnout volajícím určitou identitu při překladu odkazu.  
  
 Žádná úroveň důvěryhodnosti je spojena se silným názvem, což činí [SignTool.exe (Sign Tool)](../../framework/tools/signtool-exe.md) důležité. Tyto dva podpisové nástroje vyžadují, aby vydavatel prokázal svou identitu orgánu třetí strany a získal certifikát. Tento certifikát je pak vložen do souboru a může být použit správcem k rozhodnutí, zda důvěřovat pravosti kódu.  
  
 Můžete dát silný název a digitální podpis vytvořený pomocí [SignTool.exe (Sign Tool)](../../framework/tools/signtool-exe.md) do sestavy, nebo můžete použít buď samostatně. Dva nástroje pro podepisování mohou podepisovat pouze jeden soubor najednou. pro vícesouborové sestavení podepíšete soubor, který obsahuje manifest sestavení. Silný název je uložen v souboru obsahujícím manifest sestavení, ale podpis vytvořený pomocí [signtool.exe (Sign Tool Tool)](../../framework/tools/signtool-exe.md) je uložen ve vyhrazeném slotu v přenosném spustitelném souboru (PE), který obsahuje manifest sestavení. Podepisování sestavení pomocí [SignTool.exe (Sign Tool Tool)](../../framework/tools/signtool-exe.md) lze použít (se silným názvem nebo bez něj), pokud již máte hierarchii důvěryhodnosti, která závisí na [signtool.exe (Sign Tool)](../../framework/tools/signtool-exe.md) generované podpisy, nebo když vaše zásada používá pouze klíčovou část a nekontroluje řetězec důvěryhodnosti.  
  
> [!NOTE]
> Při použití silného názvu a podpisu podpisu podpisu podpisu nástroje pro podepisování v sestavení musí být nejprve přiřazen silný název.  
  
 Běžný jazyk runtime také provádí ověření hash; manifest sestavení obsahuje seznam všech souborů, které tvoří sestavení, včetně hash každého souboru, jak existoval, když byl vytvořen manifest. Po načtení jednotlivých souborů je z obsahu vytvořena hodnota hash a ta je porovnána s hodnotou hash uloženou v manifestu. Pokud se tyto dvě hodnoty hash neshodují, sestavení se nepodaří načíst.  
  
 Vzhledem k tomu, že silné pojmenování a podepisování pomocí [SignTool.exe (Sign Tool)](../../framework/tools/signtool-exe.md) zaručit integritu, můžete založit zásady zabezpečení přístupu kódu na tyto dvě formy evidence sestavení. Silné pojmenování a podepisování pomocí [signtool.exe (Sign Tool)](../../framework/tools/signtool-exe.md) zaručují integritu prostřednictvím digitálních podpisů a certifikátů. Všechny uvedené technologie – ověření hash, silné pojmenování a podepisování pomocí [signtool.exe (Sign Tool)](../../framework/tools/signtool-exe.md)– spolupracují, aby se zajistilo, že sestavení nebylo žádným způsobem změněno.  
  
## <a name="see-also"></a>Viz také

- [Sestavení se silným názvem](strong-named.md)
- [Sestavení v .NET](index.md)
- [SignTool.exe (nástroj pro podpis)](../../framework/tools/signtool-exe.md)
