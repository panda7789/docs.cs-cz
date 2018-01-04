---
title: "&lt;useLegacyJit&gt; – Element"
ms.custom: 
ms.date: 04/26/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d2a71e44db2d6e85ae730f4603bf191f54525c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltuselegacyjitgt-element"></a>&lt;useLegacyJit&gt; – Element

Určuje, zda modul common language runtime používá starší verze 64bitový kompilátor JIT pro kompilaci za běhu.  
  
\<Konfigurace >  
\<modul runtime >  
\<useLegacyJit >
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<useLegacyJit enabled=0|1 />
```

Název elementu `useLegacyJit` je malá a velká písmena.
  
## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
| Atribut | Popis                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | Požadovaný atribut.<br><br>Určuje, zda modul runtime používá starší verze 64bitový kompilátor JIT. |  
  
### <a name="enabled-attribute"></a>povoleno atribut  
  
| Hodnota | Popis                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | Modul CLR používá nové 64bitový JIT kompilátor zahrnuté v rozhraní .NET Framework 4.6 a novějších verzích. |  
| 1     | Modul CLR používá starší 64bitový kompilátor JIT.                                                     |  
  
### <a name="child-elements"></a>Podřízené prvky

Žádné
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
| Prvek         | Popis                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |  
| `runtime`       | Obsahuje informace o možnostech inicializace modulu runtime.                                                        |  
  
## <a name="remarks"></a>Poznámky  

Od verze rozhraní .NET Framework 4.6, modul common language runtime používá nové 64bitový kompilátor pro kompilaci JIT (JIT) ve výchozím nastavení. V některých případech může výsledkem rozdíl v chování z aplikační kód, který byl kompilována předchozí verze 64bitový kompilátor JIT. Nastavením `enabled` atribut `<useLegacyJit>` element `1`, můžete zakázat nové 64bitový kompilátor JIT a místo toho zkompilovat vaší aplikace pomocí starší verze 64bitový kompilátor JIT.  
  
> [!NOTE]
> `<useLegacyJit>` Element ovlivňuje pouze 64-bit JIT kompilace. Kompilace pomocí JIT kompilátoru 32-bit je poškozena.  
  
Místo použití souboru nastavení konfigurace, můžete povolit starší verze 64bitový kompilátor JIT dva další způsoby:  
  
- Nastavení proměnné prostředí

  Nastavte `COMPLUS_useLegacyJit` proměnnou prostředí buď `0` (použít nové 64bitový kompilátor JIT) nebo `1` (použijte starší 64bitový kompilátor JIT):
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  Proměnné prostředí má *globální obor*, což znamená, že ovlivňuje všechny aplikace spustit na počítači. Pokud nastavíte, ho bude možné přepsat pomocí souboru nastavení konfigurace aplikace. Název proměnné prostředí není malá a velká písmena.
  
- Přidání klíče registru

  Můžete povolit starší verze 64bitový kompilátor JIT přidáním `REG_DWORD` hodnota, která má buď `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` nebo `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče v registru. Hodnota jmenuje `useLegacyJit`. Pokud je hodnota 0, se používá nový kompilátoru. Pokud je hodnota 1, je starší verze 64bitový kompilátor JIT povoleno. Název hodnoty registru není malá a velká písmena.
  
  Přidáním hodnoty do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klíč ovlivní všechny aplikace spuštěné na počítači. Přidáním hodnoty do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíč ovlivní všechny aplikace spouštěné aktuálního uživatele. Pokud je počítač nakonfigurovaný s několika uživatelskými účty, jsou jenom aplikace, které spustí aktuální uživatel vliv, pokud hodnota klíče registru pro ostatní uživatele i. Přidávání `<useLegacyJit>` element konfiguračního souboru přepíše nastavení registru, pokud jsou k dispozici.  
  
## <a name="example"></a>Příklad  

Následující konfigurační soubor zakáže kompilaci s novou 64bitový kompilátor JIT a místo toho používá starší verze 64bitový kompilátor JIT.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

[\<modul runtime > elementu](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)   
[\<Konfigurace > elementu](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)   
[Omezení rizik: Nové 64-bit JIT kompilátoru](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
