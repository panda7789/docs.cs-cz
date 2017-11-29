---
title: "&lt;loadfromremotesources –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 959073381ef936fa7c0b248419c8529deaee969f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltloadfromremotesourcesgt-element"></a>&lt;loadfromremotesources –&gt; – Element
Určuje, zda sestavení ze vzdáleného zdroje udělení úplný vztah důvěryhodnosti.  
  
> [!NOTE]
>  Jestliže byly pokyn k tomuto tématu, z důvodu chybovou zprávu v seznamu chyb projektu sady Visual Studio nebo chybě sestavení, najdete v části [postupy: použití sestavení z webu v sadě Visual Studio](http://msdn.microsoft.com/en-us/d8635b63-89a0-41aa-90f4-f351b2111070).  
  
 \<Konfigurace >  
\<modul runtime >  
\<loadfromremotesources – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda sestavení, které je načtena ze vzdáleného zdroje udělení úplný vztah důvěryhodnosti.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Neudělujte úplný vztah důvěryhodnosti k aplikacím ze vzdálených zdrojů. Toto nastavení je výchozí.|  
|`true`|Udělit úplný vztah důvěryhodnosti k aplikacím ze vzdálených zdrojů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 3.5 a starší verze když se načíst sestavení ze vzdáleného umístění, sestavení spuštěná částečně důvěryhodné se sadou udělení, která závisí na zónu, ve které byla načtena. Například pokud načtení sestavení z webu ho byla načtena do zóně Internet a udělit oprávnění sadu Internet. Jinými slovy spustit v izolovaného prostoru Internetu. Pokud spustíte této sestavě [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] a novější verze, je vyvolána výjimka, musí explicitně vytvořit izolovaný prostor pro sestavení (najdete v části [postupy: spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), nebo spustit v režimu plné důvěryhodnosti.  
  
 `<loadFromRemoteSources>` Element umožňuje určit, že sestavení, která by mít spuštění částečně důvěryhodného v dřívějších verzích rozhraní .NET Framework musí být plně spuštěny v důvěryhodné [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] a novějších verzích. Ve výchozím nastavení, vzdálené sestavení se nespustí [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] a novější. Ke spuštění vzdálené sestavení, musíte buď spustit jako plně důvěryhodná nebo vytvořit v izolovaném prostoru <xref:System.AppDomain> ve kterém se má spustit.  
  
> [!NOTE]
>  V [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], sestavení na místní síťové sdílené složky jsou spustit jako úplný vztah důvěryhodnosti ve výchozím nastavení; není třeba povolit `<loadFromRemoteSources>` elementu.  
  
> [!NOTE]
>  Pokud aplikace byl zkopírován z webu, je označené v systému Windows jako webové aplikace, i v případě, že se nachází v místním počítači. Tento výběr můžete změnit změnou vlastností souboru, nebo můžete použít `<loadFromRemoteSources>` elementu, který chcete udělit sestavení úplný vztah důvěryhodnosti. Jako alternativu, můžete použít <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> metoda načíst místní sestavení, které operační systém má označení s bylo načteno z webu.  
  
 `enabled` Atributů pro tento element je platná pouze v případě, že zabezpečení přístupu kódu (CAS) je zakázaná. Ve výchozím nastavení, certifikační Autority zásada je zakázána v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] a novějších verzích. Pokud nastavíte `enabled` k `true`, vzdálené aplikace mají úplný vztah důvěryhodnosti.  
  
 Pokud `<loadFromRemoteSources>``enabled` není nastavený na `true`, je vyvolána výjimka za následujících podmínek:  
  
-   Chování sandboxing aktuální doméně se liší od jeho chování [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]. To vyžaduje zásadu CAS se zakáže a aktuální doméně není v izolovaném prostoru.  
  
-   Sestavení načítá není z `MyComputer` zóny.  
  
> [!NOTE]
>  Může dojít <xref:System.IO.FileLoadException> v aplikaci Windows Virtual PC při pokusu načíst soubor ze propojené složek na hostitelský počítač. K této chybě může dojít při pokusu načíst soubor ze složky propojené přes [služby Vzdálená plocha](http://go.microsoft.com/fwlink/?LinkId=182775) (Terminálové služby). Abyste se vyhnuli výjimku, nastavte `enabled` k `true`.  
  
 Nastavení `<loadFromRemoteSources>` element `true` zabraňuje vyvolání výjimky. Umožňuje zadat, že nejsou spoléhat na modul CLR do izolovaného prostoru načíst sestavení pro zabezpečení a že může být povolené provést jako úplný vztah důvěryhodnosti.  
  
> [!IMPORTANT]
>  Pokud sestavení by neměla běžet v režimu plné důvěryhodnosti, nenastavujte tento element konfigurace. Místo toho vytvořte v izolovaném prostoru <xref:System.AppDomain> ve kterém se načíst sestavení.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento prvek se obvykle používá v konfiguračním souboru aplikace, ale mohou být používány další konfigurační soubory v závislosti na kontextu. Další informace najdete v článku [další implicitní používá certifikační Autority zásad: loadfromremotesources –](http://go.microsoft.com/fwlink/p/?LinkId=266839) v blogu zabezpečení rozhraní .NET.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak udělit úplný vztah důvěryhodnosti k aplikacím ze vzdálených zdrojů.  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Více implicitní používá certifikační Autority zásad: loadfromremotesources –](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [Postupy: spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
