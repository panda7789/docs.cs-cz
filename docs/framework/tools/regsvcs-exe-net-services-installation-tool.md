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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 032f43aa16dbca0f4ab0477d586e7568230b7381
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044263"
---
# <a name="regsvcsexe-net-services-installation-tool"></a>Regsvcs.exe (nástroj pro instalaci služeb .NET)
Instalační nástroj .NET Services vykonává tyto akce:  
  
- Načítá a registruje sestavení.  
  
- Vytváří, registruje a instaluje knihovnu typů do zadané aplikace modelu COM+.  
  
- Konfiguruje služby, které jste přidali pomocí programu do vaší třídy.  
  
 Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).  
  
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
|*assemblyFile.dll*|Zdrojový soubor sestavení. Sestavení musí být podepsáno silným názvem. Další informace naleznete v tématu [podepisování sestavení silným názvem](../../standard/assembly/sign-strong-name.md).|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/appdir:** *cesta*|Určuje kořenový adresář aplikace.|  
|**/AppName:** *ApplicationName*|Určuje název aplikace modelu COM+, která se má vyhledat nebo vytvořit.|  
|**/c**|Vytvoří cílovou aplikaci.|  
|**/componly**|Nakonfiguruje pouze součásti; ignoruje metody a rozhraní.|  
|**/exapp**|Určuje, že nástroj má očekávat existující aplikaci.|  
|**/extlb**|Použije existující knihovnu typů.|  
|**/fc**|Vyhledá nebo vytvoří cílovou aplikaci.|  
|**/ Help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/noreconfig**|Znovu nekonfiguruje existující cílovou aplikaci.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/parName:** *název*|Určuje název nebo ID aplikace modelu COM+, která se má vyhledat nebo vytvořit.|  
|**/reconfig**|Znovu nakonfiguruje existující cílovou aplikaci. Toto nastavení je výchozí.|  
|**/TLB:** *souborKnihovnyTypů*|Určuje soubor knihovny typů instalace, který se má nainstalovat.|  
|**/u**|Odinstaluje cílovou aplikaci.|  
|**/quiet**|Určuje použití tichého režimu; potlačí zobrazování loga a zpráv o úspěchu.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Regsvcs. exe vyžaduje zdrojový soubor sestavení určený pomocí *assemblyFile. dll*. Toto sestavení musí být podepsáno silným názvem. Další informace o podepisování silným názvem naleznete v tématu [podepisování sestavení silným názvem](../../standard/assembly/sign-strong-name.md). Názvy cílové aplikace a souboru knihovny typů jsou volitelné. Argument *ApplicationName* lze vygenerovat ze zdrojového souboru sestavení a vytvoří jej pomocí Regsvcs. exe, pokud ještě neexistuje. Argument *souborKnihovnyTypů* může určovat název knihovny typů. Pokud název knihovny typů nezadáte, nástroj Regsvcs.exe použije jako výchozí název sestavení.  
  
 Pokud Regsvcs. exe zaregistruje metody komponenty, vztahuje se na ně [požadavky](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) a [požadavky propojení](../misc/link-demands.md) na tyto metody. Vzhledem k tomu, že se nástroj spouští v plně důvěryhodném prostředí, většina požadavků na oprávnění je splněna. Regsvcs. exe však nemůže registrovat součásti s metodami chráněnými požadavkem nebo odkazem <xref:System.Security.Permissions.StrongNameIdentityPermission> na aplikaci <xref:System.Security.Permissions.PublisherIdentityPermission>nebo.  
  
 Pro použití Regsvcs.exe musíte mít administrátorská oprávnění na místním počítači.  
  
 Pokud Regsvcs.exe selže při provádění kterékoli z těchto akcí, zobrazí se odpovídající chybové zprávy.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz přidá všechny veřejné třídy obsažené v `myTest.dll` do `myTargetApp` (existující `myTest.tlb` aplikace com+) a vytvoří knihovnu typů.  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 Následující příkaz přidá všechny veřejné třídy obsažené v `myTest.dll` do `myTargetApp` (existující `newTest.tlb` aplikace com+) a vytvoří knihovnu typů.  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [Postupy: Podepsat sestavení silným názvem](../../standard/assembly/sign-strong-name.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
