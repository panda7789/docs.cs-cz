---
title: "Regsvcs.exe (nástroj pro instalaci služeb .NET)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd7f50d591232feda0259ecefdb5b9e39514ccb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="regsvcsexe-net-services-installation-tool"></a>Regsvcs.exe (nástroj pro instalaci služeb .NET)
Instalační nástroj .NET Services vykonává tyto akce:  
  
-   Načítá a registruje sestavení.  
  
-   Vytváří, registruje a instaluje knihovnu typů do zadané aplikace modelu COM+.  
  
-   Konfiguruje služby, které jste přidali pomocí programu do vaší třídy.  
  
 Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*assemblyFile.dll*|Zdrojový soubor sestavení. Sestavení musí být podepsáno silným názvem. Další informace najdete v tématu [podepsání sestavení se silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/appdir:** *cesta*|Určuje kořenový adresář aplikace.|  
|**příkazy/appname:** *applicationName*|Určuje název aplikace modelu COM+, která se má vyhledat nebo vytvořit.|  
|**/c**|Vytvoří cílovou aplikaci.|  
|**0}, nejsou**|Nakonfiguruje pouze součásti; ignoruje metody a rozhraní.|  
|**/exapp**|Určuje, že nástroj má očekávat existující aplikaci.|  
|**/extlb**|Použije existující knihovnu typů.|  
|**/FC**|Vyhledá nebo vytvoří cílovou aplikaci.|  
|**/ Help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/noreconfig**|Znovu nekonfiguruje existující cílovou aplikaci.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/parname:** *název*|Určuje název nebo ID aplikace modelu COM+, která se má vyhledat nebo vytvořit.|  
|**/reconfig**|Znovu nakonfiguruje existující cílovou aplikaci. Toto nastavení je výchozí.|  
|**/ TLB:** *typelibraryfile*|Určuje soubor knihovny typů instalace, který se má nainstalovat.|  
|**/u**|Odinstaluje cílovou aplikaci.|  
|**/quiet**|Určuje použití tichého režimu; potlačí zobrazování loga a zpráv o úspěchu.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 RegSvcs.exe vyžaduje zdrojového souboru sestavení určeného *assemblyFile.dll*. Toto sestavení musí být podepsáno silným názvem. Další informace o podepisování silným názvem naleznete v tématu [podepsání sestavení se silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md). Názvy cílové aplikace a souboru knihovny typů jsou volitelné. *ApplicationName* argument může být generována ze zdrojového souboru sestavení a vytvoří Regsvcs.exe, pokud ještě neexistuje. *Typelibraryfile* argument můžete zadat název typu knihovny. Pokud název knihovny typů nezadáte, nástroj Regsvcs.exe použije jako výchozí název sestavení.  
  
 Při Regsvcs.exe zaregistruje komponenty metody, je podléhají [požadavky](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48) a [požadavky na propojení](../../../docs/framework/misc/link-demands.md) na těchto metod. Vzhledem k tomu, že se nástroj spouští v plně důvěryhodném prostředí, většina požadavků na oprávnění je splněna. Regsvcs.exe však nelze zaregistrovat součásti pomocí metod, které jsou chráněny požadavku na vyžádání nebo odkaz pro <xref:System.Security.Permissions.StrongNameIdentityPermission> nebo <xref:System.Security.Permissions.PublisherIdentityPermission>.  
  
 Pro použití Regsvcs.exe musíte mít administrátorská oprávnění na místním počítači.  
  
 Pokud Regsvcs.exe selže při provádění kterékoli z těchto akcí, zobrazí se odpovídající chybové zprávy.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz přidá všechny veřejné třídy, které jsou obsažené v `myTest.dll` k `myTargetApp` (stávající modelu COM + aplikaci) a vytvoří `myTest.tlb` knihovny typů.  
  
```  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 Následující příkaz přidá všechny veřejné třídy, které jsou obsažené v `myTest.dll` k `myTargetApp` (stávající modelu COM + aplikaci) a vytvoří `newTest.tlb` knihovny typů.  
  
```  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Postupy: Podepsání sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
