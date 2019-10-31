---
title: Element <shadowCopyVerifyByTimestamp>
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: 160f14c856735e1ceac8635506aea52454faea43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115731"
---
# <a name="shadowcopyverifybytimestamp-element"></a>\<element > shadowCopyVerifyByTimestamp
Určuje, zda stínové kopírování používá výchozí chování při spuštění, které bylo zavedeno ve .NET Framework 4, nebo se vrátí k chování při spuštění starších verzí .NET Framework.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<shadowCopyVerifyByTimestamp >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|umožněn|Požadovaný atribut.<br /><br /> Určuje, zda aplikační domény, které používají stínové kopírování, porovnávají časová razítka sestavení při spuštění, aby bylo možné určit, zda bylo sestavení Aktualizováno před stínovým kopírováním sestavení.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|true|Při spuštění nástroje kopíruje pouze sestavení, která byla aktualizována od posledního zkopírování do adresáře stínové kopie. Toto je výchozí nastavení pro .NET Framework 4.|  
|false|Vrátí se k chování při spuštění předchozích verzí .NET Framework, což bylo při spuštění zkopírovat všechny soubory.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje .NET Framework 4 jsou sestavení Stínová zkopírována pouze v případě, že jejich časová razítka signalizují, že se od posledního zkopírování do adresáře stínové kopie změnily. To zlepšuje dobu spouštění pro mnoho aplikací, které používají stínové kopírování, jak je popsáno v tématu [stínové kopírování sestavení](../../../app-domains/shadow-copy-assemblies.md). Aplikace, které mají vysoké procento a četnost aktualizací sestavení, nemusí mít tuto změnu v chování. V takovém případě můžete použít tento prvek k obnovení chování předchozích verzí .NET Framework.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat výchozí chování při spouštění stínového kopírování v .NET Framework 4 a vrátit se k chování při spuštění předchozích verzí .NET Framework.  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Stínové kopírování sestavení](../../../app-domains/shadow-copy-assemblies.md)
