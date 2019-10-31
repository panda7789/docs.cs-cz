---
title: Element <enforceFIPSPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
ms.openlocfilehash: 0d6dd291a24928487a040c0427f058dee80bf836
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117376"
---
# <a name="enforcefipspolicy-element"></a>\<element > enforceFIPSPolicy
Určuje, jestli se má vymáhat požadavek na konfiguraci počítače, který kryptografické algoritmy musí dodržovat Standard FIPS (Federal Information Processing Standards).  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<enforceFIPSPolicy >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|umožněn|Požadovaný atribut.<br /><br /> Určuje, jestli se má povolit vynucení požadavku na konfiguraci počítače, že kryptografické algoritmy musí být kompatibilní se standardem FIPS.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`true`|Pokud je počítač nakonfigurován tak, aby vyžadoval kryptografické algoritmy kompatibilní se standardem FIPS, bude tento požadavek vynucen. Pokud třída implementuje algoritmus, který není kompatibilní se standardem FIPS, konstruktory nebo metody `Create` pro tuto třídu vyvolávají výjimky při jejich spuštění na daném počítači. Toto nastavení je výchozí.|  
|`false`|Kryptografické algoritmy, které aplikace používá, nemusí být kompatibilní se standardem FIPS bez ohledu na konfiguraci počítače.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje .NET Framework 2,0 se vytváření tříd, které implementují kryptografické algoritmy, řídí konfigurací počítače. Pokud je počítač nakonfigurován tak, aby vyžadoval, aby algoritmy byly kompatibilní se standardem FIPS, a třída implementuje algoritmus, který není kompatibilní se standardem FIPS, jakýkoli pokus o vytvoření instance této třídy vyvolá výjimku. Konstruktory vyvolávají výjimku <xref:System.InvalidOperationException> a metody `Create` vyvolávají výjimku <xref:System.Reflection.TargetInvocationException> s vnitřní výjimkou <xref:System.InvalidOperationException>.  
  
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
