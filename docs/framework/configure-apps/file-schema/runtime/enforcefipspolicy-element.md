---
title: Element <enforceFIPSPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f90abf9f6c2bc0aed2cf01558b2c0cca4e967e81
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252637"
---
# <a name="enforcefipspolicy-element"></a>\<enforceFIPSPolicy – element >
Určuje, jestli se má vymáhat požadavek na konfiguraci počítače, který kryptografické algoritmy musí dodržovat Standard FIPS (Federal Information Processing Standards).  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<enforceFIPSPolicy>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|enabled|Požadovaný atribut.<br /><br /> Určuje, jestli se má povolit vynucení požadavku na konfiguraci počítače, že kryptografické algoritmy musí být kompatibilní se standardem FIPS.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|`true`|Pokud je počítač nakonfigurován tak, aby vyžadoval kryptografické algoritmy kompatibilní se standardem FIPS, bude tento požadavek vynucen. Pokud třída implementuje algoritmus, který není kompatibilní se standardem FIPS, konstruktory nebo `Create` metody této třídy vyvolávají výjimky při jejich spuštění na daném počítači. Toto nastavení je výchozí.|  
|`false`|Kryptografické algoritmy, které aplikace používá, nemusí být kompatibilní se standardem FIPS bez ohledu na konfiguraci počítače.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje .NET Framework 2,0 se vytváření tříd, které implementují kryptografické algoritmy, řídí konfigurací počítače. Pokud je počítač nakonfigurován tak, aby vyžadoval, aby algoritmy byly kompatibilní se standardem FIPS, a třída implementuje algoritmus, který není kompatibilní se standardem FIPS, jakýkoli pokus o vytvoření instance této třídy vyvolá výjimku. Konstruktory vyvolávají <xref:System.InvalidOperationException> výjimku a `Create` metody vyvolávají <xref:System.Reflection.TargetInvocationException> výjimku s vnitřní <xref:System.InvalidOperationException> výjimkou.  
  
 Pokud vaše aplikace běží na počítačích, jejichž konfigurace vyžaduje kompatibilitu se standardem FIPS, a vaše aplikace používá algoritmus, který není kompatibilní se standardem FIPS, můžete použít tento prvek v konfiguračním souboru, aby nedocházelo k tomu, že modul CLR (Common Language Runtime) z vynucování dodržování standardů FIPS. Tento prvek byl představen v aktualizaci Service Pack 1 pro .NET Framework 2,0.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zabránit CLR v vynucování dodržování standardů FIPS.  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Kryptografický model](../../../../standard/security/cryptography-model.md)
