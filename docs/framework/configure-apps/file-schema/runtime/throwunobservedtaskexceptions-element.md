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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153812"
---
# <a name="throwunobservedtaskexceptions-element"></a>Element \<ThrowUnobservedTaskExceptions>
Určuje, zda výjimky neošetřených úloh mají ukončit běžící proces.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda mají být neošetřené výjimky úloh ukončeny spuštěným procesem.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Description|  
|-----------|-----------------|  
|`false`|Neukončí běžící proces pro neošetřenou výjimku úlohy. Toto nastavení je výchozí.|  
|`true`|Ukončí běžící proces pro neošetřenou výjimku úlohy.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
|||  
  
## <a name="remarks"></a>Poznámky  
 Pokud nebyla pozorována výjimka, která je přidružena k objektu, není k <xref:System.Threading.Tasks.Task> dispozici žádná <xref:System.Threading.Tasks.Task.Wait%2A> operace, nadřazený objekt není připojen a <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> vlastnost nebyla přečtena. výjimka úlohy je považována za nepozorovanou.  
  
 V .NET Framework 4 ve výchozím nastavení, pokud <xref:System.Threading.Tasks.Task> má výjimku s nepozorovanou výjimkou uvolňování paměti, finalizační metoda vyvolá výjimku a ukončí proces. Ukončení procesu je určeno časováním uvolňování paměti a dokončením.  
  
 Aby vývojáři usnadnili psaní asynchronního kódu založeného na úlohách, .NET Framework 4,5 mění toto výchozí chování pro nepozorované výjimky. Nepozorované výjimky stále způsobují <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> vyvolání události, ale ve výchozím nastavení se proces neukončí. Místo toho je výjimka po vyvolání události ignorována bez ohledu na to, zda obslužná rutina události tuto výjimku dobere.  
  
 V .NET Framework 4,5 lze použít [ \<ThrowUnobservedTaskExceptions> prvek](throwunobservedtaskexceptions-element.md) v konfiguračním souboru aplikace, chcete-li povolit chování .NET Framework 4 při vyvolání výjimky.  
  
 Chování výjimky můžete určit také jedním z následujících způsobů:  
  
- Nastavením proměnné prostředí `COMPlus_ThrowUnobservedTaskExceptions` ( `set COMPlus_ThrowUnobservedTaskExceptions=1` ).  
  
- Nastavením hodnoty DWORD registru ThrowUnobservedTaskExceptions = 1 v HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework klíč.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak povolit vyvolávání výjimek v úlohách pomocí konfiguračního souboru aplikace.  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak je vyvolána nepozorovaná výjimka z úlohy. Kód musí být spuštěn jako vydaný program pro správné fungování.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
