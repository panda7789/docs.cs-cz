---
title: Element <useLegacyJit>
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
ms.openlocfilehash: a126b8c0050a8d1fd96a3d090f9b018a9faa07a7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968859"
---
# <a name="uselegacyjit-element"></a>Element \<useLegacyJit>

Určuje, zda modul CLR (Common Language Runtime) používá starší 64 kompilátor JIT pro kompilaci za běhu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<useLegacyJit enabled=0|1 />
```

V názvu elementu `useLegacyJit` se rozlišují velká a malá písmena.
  
## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
| Atribut | Popis                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | Požadovaný atribut.<br><br>Určuje, zda modul runtime používá starší 64 kompilátor JIT. |  
  
### <a name="enabled-attribute"></a>povolený atribut  
  
| Hodnota | Description                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | Modul CLR (Common Language Runtime) používá nový 64 kompilátor JIT zahrnutý v .NET Framework 4,6 a novějších verzích. |  
| 1     | Modul common language runtime používá starší 64 kompilátor JIT.                                                     |  
  
### <a name="child-elements"></a>Podřízené prvky

Žádné
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
| Prvek         | Description                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |  
| `runtime`       | Obsahuje informace o možnostech inicializace modulu runtime.                                                        |  
  
## <a name="remarks"></a>Poznámky  

Počínaje .NET Framework 4,6 používá modul CLR (Common Language Runtime) nový 64 kompilátor pro kompilaci JIT (just-in-time) ve výchozím nastavení. V některých případech to může vést k rozdílu v chování z kódu aplikace, který byl zkompilován JIT pomocí předchozí verze 64 kompilátoru JIT. Nastavením `enabled` atributu `<useLegacyJit>` elementu na `1` můžete zakázat nový 64 kompilátor JIT a místo toho zkompilovat aplikaci pomocí starší verze 64 kompilátoru JIT.  
  
> [!NOTE]
> `<useLegacyJit>`Element ovlivňuje pouze 64 KOMPILACI JIT. Kompilace s 32 kompilátorem JIT není nijak ovlivněna.  
  
Namísto použití nastavení konfiguračního souboru můžete povolit starší 64 kompilátor JIT dvěma způsoby:  
  
- Nastavení proměnné prostředí

  Nastavte `COMPLUS_useLegacyJit` proměnnou prostředí na buď `0` (použijte nový 64 kompilátor JIT), nebo `1` (použijte starší 64 kompilátor JIT):
  
  ```env  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  Proměnná prostředí má *globální rozsah*, což znamená, že má vliv na všechny aplikace spuštěné v počítači. Pokud je tato hodnota nastavena, může být přepsána nastavením konfiguračního souboru aplikace. V názvu proměnné prostředí se nerozlišují velká a malá písmena.
  
- Přidání klíče registru

  Můžete povolit starší 64 kompilátor JIT přidáním `REG_DWORD` hodnoty do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče nebo v registru. Hodnota je pojmenována `useLegacyJit` . Je-li hodnota 0, je použit nový kompilátor. Pokud je hodnota 1, je povolen starší 64 kompilátor JIT. V názvu hodnoty registru se nerozlišují malá a velká písmena.
  
  Přidání hodnoty do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klíče má vliv na všechny aplikace spuštěné v počítači. Přidání hodnoty do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče má vliv na všechny aplikace spuštěné aktuálním uživatelem. Pokud je počítač nakonfigurovaný s několika uživatelskými účty, ovlivní se jenom aplikace spuštěné aktuálním uživatelem, pokud se hodnota nepřidá do klíčů registru pro ostatní uživatele. Přidání `<useLegacyJit>` elementu do konfiguračního souboru přepíše nastavení registru, pokud jsou k dispozici.  
  
## <a name="example"></a>Příklad  

Následující konfigurační soubor zakáže kompilaci s novým 64 kompilátorem JIT a místo toho používá starší 64 kompilátor JIT.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- [\<runtime>Objekt](runtime-element.md)
- [\<configuration>Objekt](../configuration-element.md)
- [Zmírnění: nový 64 kompilátor JIT](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
