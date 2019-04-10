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
ms.openlocfilehash: 1b529ccd8c5e0cf0563adf556a7d316372ac4d0e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215037"
---
# <a name="regsvcsexe-net-services-installation-tool"></a>Regsvcs.exe (nástroj pro instalaci služeb .NET)
Instalační nástroj .NET Services vykonává tyto akce:  
  
-   Načítá a registruje sestavení.  
  
-   Vytváří, registruje a instaluje knihovnu typů do zadané aplikace modelu COM+.  
  
-   Konfiguruje služby, které jste přidali pomocí programu do vaší třídy.  
  
 Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*assemblyFile.dll*|Zdrojový soubor sestavení. Sestavení musí být podepsáno silným názvem. Další informace najdete v tématu [podepisování sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/appdir:** *cesta*|Určuje kořenový adresář aplikace.|  
|**příkazy/appname:** *applicationName*|Určuje název aplikace modelu COM+, která se má vyhledat nebo vytvořit.|  
|**/c**|Vytvoří cílovou aplikaci.|  
|**/componly**|Nakonfiguruje pouze součásti; ignoruje metody a rozhraní.|  
|**/exapp**|Určuje, že nástroj má očekávat existující aplikaci.|  
|**/extlb**|Použije existující knihovnu typů.|  
|**/fc**|Vyhledá nebo vytvoří cílovou aplikaci.|  
|**/help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/noreconfig**|Znovu nekonfiguruje existující cílovou aplikaci.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/parname:** *název*|Určuje název nebo ID aplikace modelu COM+, která se má vyhledat nebo vytvořit.|  
|**/reconfig**|Znovu nakonfiguruje existující cílovou aplikaci. Toto nastavení je výchozí.|  
|**/ TLB:** *souborknihovnytypů*|Určuje soubor knihovny typů instalace, který se má nainstalovat.|  
|**/u**|Odinstaluje cílovou aplikaci.|  
|**/quiet**|Určuje použití tichého režimu; potlačí zobrazování loga a zpráv o úspěchu.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 RegSvcs.exe vyžaduje zdrojový soubor sestavení určený *assemblyFile.dll*. Toto sestavení musí být podepsáno silným názvem. Další informace o podepisování silným názvem naleznete v tématu [podepisování sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md). Názvy cílové aplikace a souboru knihovny typů jsou volitelné. *ApplicationName* argument se dá vygenerovat na zdrojový soubor sestavení a, bude vytvořen pomocí Regsvcs.exe, pokud ještě neexistuje. *Souborknihovnytypů* argument můžete zadat název knihovny typů. Pokud název knihovny typů nezadáte, nástroj Regsvcs.exe použije jako výchozí název sestavení.  
  
 Pokud Regsvcs.exe registruje metody, se vztahuje [požadavky](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) a [požadavky na propojení](../../../docs/framework/misc/link-demands.md) na tyto metody. Vzhledem k tomu, že se nástroj spouští v plně důvěryhodném prostředí, většina požadavků na oprávnění je splněna. Regsvcs.exe však nemůže zaregistrovat prvky pomocí metod chráněných požadavkem nebo odkazem pro <xref:System.Security.Permissions.StrongNameIdentityPermission> nebo <xref:System.Security.Permissions.PublisherIdentityPermission>.  
  
 Pro použití Regsvcs.exe musíte mít administrátorská oprávnění na místním počítači.  
  
 Pokud Regsvcs.exe selže při provádění kterékoli z těchto akcí, zobrazí se odpovídající chybové zprávy.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz přidá všechny veřejné třídy obsažené v `myTest.dll` k `myTargetApp` (existující aplikace modelu COM +) a vytvoří `myTest.tlb` knihovny typů.  
  
```  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 Následující příkaz přidá všechny veřejné třídy obsažené v `myTest.dll` k `myTargetApp` (existující aplikace modelu COM +) a vytvoří `newTest.tlb` knihovny typů.  
  
```  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Postupy: Podepsání sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
