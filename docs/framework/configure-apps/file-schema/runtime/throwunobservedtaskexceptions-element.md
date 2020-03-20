---
title: Element <ThrowUnobservedTaskExceptions>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153812"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<Prvek> nepozorovaných úloh
Určuje, zda mají neošetřené výjimky úloh ukončit spuštěný proces.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda mají neošetřené výjimky úloh ukončit spuštěný proces.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Neukončí spuštěný proces pro výjimku neošetřené úlohy. Toto nastavení je výchozí.|  
|`true`|Ukončí spuštěný proces pro výjimku neošetřených úloh.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
|||  
  
## <a name="remarks"></a>Poznámky  
 Pokud nebyla dodržena <xref:System.Threading.Tasks.Task> výjimka, která je <xref:System.Threading.Tasks.Task.Wait%2A> přidružena k a, neexistuje <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> žádná operace, nadřazená možnost není připojena a vlastnost nebyla přečtena, je výjimka úkolu považována za nedodrženou.  
  
 V rozhraní .NET Framework 4 ve <xref:System.Threading.Tasks.Task> výchozím nastavení, pokud a, který má nepozorované výjimky je uvolněna, finalizační metoda vyvolá výjimku a ukončí proces. Ukončení procesu je určena načasování uvolňování paměti a dokončení.  
  
 Chcete-li usnadnit vývojářům psát asynchronní kód na základě úkolů, rozhraní .NET Framework 4.5 změní toto výchozí chování pro nepozorované výjimky. Nepozorované výjimky <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> stále způsobit událost, která má být vyvolána, ale ve výchozím nastavení proces neukončí. Místo toho je výjimka ignorována po vyvolání události, bez ohledu na to, zda obslužná rutina události dodržuje výjimku.  
  
 V rozhraní .NET Framework 4.5 můžete použít [ \<prvek> ThrowUnobservedTaskExceptions](throwunobservedtaskexceptions-element.md) v konfiguračním souboru aplikace k povolení chování rozhraní .NET Framework 4 vyvolání výjimky.  
  
 Chování výjimek můžete také určit jedním z následujících způsobů:  
  
- Nastavením proměnné `COMPlus_ThrowUnobservedTaskExceptions` prostředí`set COMPlus_ThrowUnobservedTaskExceptions=1`( ).  
  
- Nastavením hodnoty DWORD registru ThrowUnobservedTaskExceptions = 1 v\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak povolit vyvolání výjimek v úlohách pomocí konfiguračního souboru aplikace.  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak je vyvolána nepozorovaná výjimka z úkolu. Kód musí být spuštěn jako uvolněný program, aby fungoval správně.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
