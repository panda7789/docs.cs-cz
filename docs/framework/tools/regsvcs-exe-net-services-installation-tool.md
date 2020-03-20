---
title: Regsvcs.exe (nástroj pro instalaci služeb .NET)
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: aecd2f6894558b45898c7f22dd333617d9e2e327
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180365"
---
# <a name="regsvcsexe-net-services-installation-tool"></a>Regsvcs.exe (nástroj pro instalaci služeb .NET)
Instalační nástroj .NET Services vykonává tyto akce:  
  
- Načítá a registruje sestavení.  
  
- Vytváří, registruje a instaluje knihovnu typů do zadané aplikace modelu COM+.  
  
- Konfiguruje služby, které jste přidali pomocí programu do vaší třídy.  
  
 Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*soubor assemblyFile.dll*|Zdrojový soubor sestavení. Sestavení musí být podepsáno silným názvem. Další informace naleznete [v tématu Podepsání sestavení se silným názvem](../../standard/assembly/sign-strong-name.md).|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/appdir:** *cesta*|Určuje kořenový adresář aplikace.|  
|**/appname:** *applicationName*|Určuje název aplikace modelu COM+, která se má vyhledat nebo vytvořit.|  
|**/c**|Vytvoří cílovou aplikaci.|  
|**/componly**|Nakonfiguruje pouze součásti; ignoruje metody a rozhraní.|  
|**/exapp**|Určuje, že nástroj má očekávat existující aplikaci.|  
|**/extlb**|Použije existující knihovnu typů.|  
|**/fc**|Vyhledá nebo vytvoří cílovou aplikaci.|  
|**/nápověda**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/noreconfig**|Znovu nekonfiguruje existující cílovou aplikaci.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/parname:** *název*|Určuje název nebo ID aplikace modelu COM+, která se má vyhledat nebo vytvořit.|  
|**/reconfig**|Znovu nakonfiguruje existující cílovou aplikaci. Toto nastavení je výchozí.|  
|**/tlb:** *soubor typelibraryfile*|Určuje soubor knihovny typů instalace, který se má nainstalovat.|  
|**/u**|Odinstaluje cílovou aplikaci.|  
|**/tichý**|Určuje použití tichého režimu; potlačí zobrazování loga a zpráv o úspěchu.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Program Regsvcs.exe vyžaduje zdrojový soubor sestavení určený souborem *assemblyFile.dll*. Toto sestavení musí být podepsáno silným názvem. Další informace o podepisování silného názvu naleznete [v tématu Podepsání sestavení se silným názvem](../../standard/assembly/sign-strong-name.md). Názvy cílové aplikace a souboru knihovny typů jsou volitelné. Argument *applicationName* může být generován ze zdrojového souboru sestavení a bude vytvořen programem Regsvcs.exe, pokud ještě neexistuje. Argument *typelibraryfile* může určit název knihovny typů. Pokud název knihovny typů nezadáte, nástroj Regsvcs.exe použije jako výchozí název sestavení.  
  
 Když Regsvcs.exe registruje metody komponenty, podléhá [požadavkům](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) a [požadavkům](../misc/link-demands.md) na propojení těchto metod. Vzhledem k tomu, že se nástroj spouští v plně důvěryhodném prostředí, většina požadavků na oprávnění je splněna. Program Regsvcs.exe však nemůže registrovat součásti pomocí metod <xref:System.Security.Permissions.StrongNameIdentityPermission> chráněných poptávkou nebo propojením poptávky <xref:System.Security.Permissions.PublisherIdentityPermission>pro soubor .  
  
 Pro použití Regsvcs.exe musíte mít administrátorská oprávnění na místním počítači.  
  
 Pokud Regsvcs.exe selže při provádění kterékoli z těchto akcí, zobrazí se odpovídající chybové zprávy.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz přidá všechny veřejné `myTest.dll` třídy obsažené v `myTargetApp` (existující aplikace `myTest.tlb` modelu COM+) a vytvoří knihovnu typů.  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 Následující příkaz přidá všechny veřejné `myTest.dll` třídy obsažené v `myTargetApp` (existující aplikace `newTest.tlb` modelu COM+) a vytvoří knihovnu typů.  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Postupy: Podepsání sestavení silným názvem](../../standard/assembly/sign-strong-name.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
