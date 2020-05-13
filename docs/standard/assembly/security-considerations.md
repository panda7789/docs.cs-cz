---
title: Důležité informace o zabezpečení sestavení
description: Při sestavování sestavení .NET můžete zadat oprávnění, která sestavení vyžaduje ke spuštění. Tento článek popisuje sestavení se silným názvem a nástroje pro podepisování.
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
ms.openlocfilehash: 7f897241b121cf1bd52d02ee5f487aeafafc3cb0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378662"
---
# <a name="assembly-security-considerations"></a>Důležité informace o zabezpečení sestavení
Při sestavování sestavení můžete zadat sadu oprávnění, které sestavení vyžaduje ke spuštění. Zda jsou určitá oprávnění udělena nebo nejsou udělena sestavení, založena na legitimaci.  
  
 K dispozici jsou dva způsoby, jak se legitimace používá:  
  
- Vstupní legitimace se sloučí s legitimací shromážděnými zavaděčem a vytvoří finální sadu legitimace, která se používá pro řešení zásad. Metody, které používají tuto sémantickou sémantiku, zahrnují **Assembly. Load**, **Assembly. LoadFrom**a **Activator. CreateInstance**.  
  
- Vstupní legitimace se nezměnila jako konečná sada legitimace, která se používá pro řešení zásad. Metody, které používají tuto sémantickou sémantiku, zahrnují **Assembly. Load (Byte [])** a **AppDomain. DefineDynamicAssembly ()**.  
  
  Volitelná oprávnění mohou být udělena [zásadami zabezpečení](../../framework/misc/code-access-security-basics.md) nastavenými v počítači, kde bude sestavení spuštěno. Pokud chcete, aby váš kód zpracovával všechny potenciální výjimky zabezpečení, můžete provést jednu z následujících akcí:  
  
- Vložte žádost o oprávnění pro všechna oprávnění, která váš kód musí mít, a zajistěte, aby se před tím, než se udělí oprávnění, nastavila zpráva o selhání při načtení.  
  
- Nepoužívejte žádost o oprávnění k získání oprávnění, která může váš kód potřebovat, ale připraví se pro zpracování výjimek zabezpečení, pokud nejsou udělená oprávnění.  
  
  > [!NOTE]
  > Zabezpečení je složitá oblast a máte spoustu možností, jak vybírat. Další informace najdete v tématu [klíčové koncepty zabezpečení](../../standard/security/key-security-concepts.md).  
  
 V době načítání se legitimace sestavení používá jako vstup do zásad zabezpečení. Zásady zabezpečení jsou zřízené podnikem a správcem počítače a také nastavením zásad uživatele a určují sadu oprávnění, která jsou udělena všem spravovaným kód při spuštění. Zásady zabezpečení lze zřídit pro vydavatele sestavení (Pokud má podpis vygenerovaný nástrojem pro podpis), pro web a zónu (v terminologii aplikace Internet Explorer), ze kterého bylo sestavení staženo nebo pro silný název sestavení. Správce počítače může například vytvořit zásadu zabezpečení, která umožňuje veškerý kód stažený z webu a podepsaný danou softwarovou společností pro přístup k databázi v počítači, ale neuděluje přístup k zápisu do disku počítače.  
  
## <a name="strong-named-assemblies-and-signing-tools"></a>Sestavení a nástroje pro podepisování se silným názvem  

 > [!WARNING]
 > Nespoléhá se na silné názvy zabezpečení. Poskytují pouze jedinečnou identitu.

 Sestavení můžete podepsat dvěma různými způsoby, ale s použitím silného názvu nebo pomocí [nástroje SignTool. exe (Sign Tool)](../../framework/tools/signtool-exe.md). Podepsání sestavení silným názvem přidá šifrování pomocí veřejného klíče do souboru obsahujícího manifest sestavení. Podepisování silným názvem pomáhá ověřit jedinečnost názvu, zabránit falšování názvů a poskytovat volajícím s určitou identitou, když se odkaz vyřeší.  
  
 Není k dispozici žádná úroveň důvěryhodnosti se silným názvem, který je důležitý pro [Nástroj SignTool. exe (Sign Tool)](../../framework/tools/signtool-exe.md) . Dva podpisové nástroje vyžadují, aby Vydavatel prokázal svoji identitu autoritě třetí strany a získal certifikát. Tento certifikát je pak vložen do souboru a může ho použít správce k rozhodnutí, jestli chcete důvěřovat pravosti kódu.  
  
 Můžete zadat silný název a digitální podpis vytvořený pomocí [nástroje SignTool. exe (Sign Tool)](../../framework/tools/signtool-exe.md) do sestavení nebo můžete použít samostatně. Pomocí obou podpisových nástrojů lze současně podepsat pouze jeden soubor. pro vícesouborové sestavení podepište soubor, který obsahuje manifest sestavení. Silný název je uložen v souboru obsahujícím manifest sestavení, ale signatura vytvořená pomocí [nástroje SignTool. exe (Sign Tool)](../../framework/tools/signtool-exe.md) je uložena v přenosném spustitelném souboru (PE), který obsahuje manifest sestavení. Podpis sestavení pomocí [nástroje SignTool. exe (Nástroj pro podepsání)](../../framework/tools/signtool-exe.md) lze použít (s nebo bez silného názvu), pokud již máte hierarchii důvěryhodnosti, která spoléhá na signatury vygenerované pomocí [nástroje SignTool. exe (Sign Tool)](../../framework/tools/signtool-exe.md) , nebo když vaše zásada používá pouze část klíče a nekontroluje řetěz důvěryhodnosti.  
  
> [!NOTE]
> Při použití silného názvu a podpisu podpisového nástroje v sestavení musí být nejprve přiřazen silný název.  
  
 Modul CLR (Common Language Runtime) také provádí ověřování hodnot hash; manifest sestavení obsahuje seznam všech souborů, ze kterých se sestaví sestavení, včetně hash každého souboru, který existoval při sestavení manifestu. Po načtení jednotlivých souborů je z obsahu vytvořena hodnota hash a ta je porovnána s hodnotou hash uloženou v manifestu. Pokud se tyto dvě hodnoty hash neshodují, sestavení se nepodaří načíst.  
  
 Vzhledem k tomu, že silné přidělování názvů a podepisování pomocí [nástroje SignTool. exe (Sign Tool)](../../framework/tools/signtool-exe.md) zaručuje integritu, můžete zásady zabezpečení přístupu ke kódu použít na těchto dvou formulářích legitimace sestavení. Silné pojmenování a podepisování pomocí [nástroje SignTool. exe (Sign Tool)](../../framework/tools/signtool-exe.md) zaručuje integritu prostřednictvím digitálních podpisů a certifikátů. Všechny zmíněné technologie – ověřování hodnoty hash, silné pojmenování a podepisování pomocí [nástroje SignTool. exe (Sign Tool)](../../framework/tools/signtool-exe.md)– Pracujte společně, aby bylo zajištěno, že sestavení nebylo nijak změněno.  
  
## <a name="see-also"></a>Viz také

- [Sestavení se silným názvem](strong-named.md)
- [Sestavení v .NET](index.md)
- [SignTool. exe (Nástroj pro podepsání)](../../framework/tools/signtool-exe.md)
