---
title: '&lt;useLegacyJit&gt; – Element'
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd4f9728338ecc66f84fe42b9bdbda9938ed518b
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612189"
---
# <a name="ltuselegacyjitgt-element"></a>&lt;useLegacyJit&gt; – Element

Určuje, zda modul common language runtime používá starší verzi 64bitového kompilátoru JIT kompilace just-in-time.  
  
\<Konfigurace >  
\<modul runtime >  
\<useLegacyJit >
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<useLegacyJit enabled=0|1 />
```

Název elementu `useLegacyJit` velká a malá písmena.
  
## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
| Atribut | Popis                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | Požadovaný atribut.<br><br>Určuje, zda modul runtime používá starší verzi 64bitového kompilátoru JIT. |  
  
### <a name="enabled-attribute"></a>Atribut enabled  
  
| Hodnota | Popis                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | Modul common language runtime používá nový kompilátor JIT 64-bit zahrnuty v rozhraní .NET Framework 4.6 a novějších verzích. |  
| 1     | Modul common language runtime používá starší 64bitovým kompilátorem JIT.                                                     |  
  
### <a name="child-elements"></a>Podřízené prvky

Žádná
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
| Prvek         | Popis                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |  
| `runtime`       | Obsahuje informace o možnostech inicializace modulu runtime.                                                        |  
  
## <a name="remarks"></a>Poznámky  

Od verze rozhraní .NET Framework 4.6, modul common language runtime používá nový 64bitový kompilátor pro kompilaci za běhu (JIT) ve výchozím nastavení. V některých případech to může vést rozdíl v chování od kódu aplikace, který byl zkompilován JIT Kompilátorem v předchozí verzi 64bitového kompilátoru JIT. Tím, že nastavíte `enabled` atribut `<useLegacyJit>` element `1`, můžete zakázat nového 64bitového kompilátoru JIT a místo toho zkompilujte aplikaci pomocí starší verze 64bitovým kompilátorem JIT.  
  
> [!NOTE]
> `<useLegacyJit>` Element ovlivňuje pouze kompilaci JIT 64-bit. Kompilace s kompilátorem JIT 32 bitů je poškozena.  
  
Namísto použití souboru nastavení konfigurace, můžete povolit starší verzi 64bitového kompilátoru JIT dvěma dalšími způsoby:  
  
- Nastavení proměnné prostředí

  Nastavte `COMPLUS_useLegacyJit` proměnnou prostředí, aby buď `0` (použití nového 64bitového kompilátoru JIT) nebo `1` (použijte starší 64bitového kompilátoru JIT):
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  Proměnná prostředí má *globálním rozsahem*, což znamená, že to má vliv na všechny aplikace, spusťte na počítači. Pokud nastavit, je možné přepsat nastavení konfiguračního souboru aplikace. Název proměnné prostředí není malá a velká písmena.
  
- Přidání klíče registru

  Můžete povolit starší verzi 64bitového kompilátoru JIT tak, že přidáte `REG_DWORD` hodnota, která má buď `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` nebo `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče v registru. Hodnota jmenuje `useLegacyJit`. Pokud je hodnota 0, použije se nový kompilátor. Pokud je hodnota 1, starší verzi 64bitového kompilátoru JIT je povolená. Název hodnoty registru není malá a velká písmena.
  
  Přidání hodnoty `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klíč má vliv na všechny aplikace spuštěné na počítači. Přidání hodnoty `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíč má vliv na všechny aplikace, které se spustí aktuální uživatel. Pokud počítač je nakonfigurovaný s několika uživatelskými účty, ovlivníte jenom aplikace, které aktuální uživatel spouštět, pokud hodnota je přidána do klíče registru pro ostatní uživatele také. Přidávání `<useLegacyJit>` prvku do konfiguračního souboru přepíše nastavení registru v případě, že jsou k dispozici.  
  
## <a name="example"></a>Příklad  

Následující konfigurační soubor zakazuje kompilaci pomocí nového 64bitového kompilátoru JIT a místo toho používá starší verzi 64bitového kompilátoru JIT.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [\<modul runtime > – Element](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)   
- [\<Konfigurace > – Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)   
- [Omezení rizik: Nový kompilátor JIT 64-bit](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
