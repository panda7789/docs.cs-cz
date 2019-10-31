---
title: Element <publisherPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
ms.openlocfilehash: 89fa8a991cc7d0352eb0a13cdfd3a6063ea468e7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115848"
---
# <a name="publisherpolicy-element"></a>\<element > publisherPolicy
Určuje, zda modul runtime používá zásady vydavatele.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dependentAssembly >** ](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<publisherPolicy >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`apply`|Určuje, jestli se mají použít zásady vydavatele.|  
  
## <a name="apply-attribute"></a>použít atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`yes`|Použije zásady vydavatele. Toto je výchozí nastavení.|  
|`no`|Nepoužívá zásadu vydavatele.|  
  
### <a name="child-elements"></a>Podřízené elementy  

Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`assemblyBinding`|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`dependentAssembly`|Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení. Pro každé sestavení použijte jeden `<dependentAssembly>` element.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Když dodavatel komponenty uvolní novou verzi sestavení, dodavatel může zahrnout zásadu vydavatele, aby aplikace, které používají starou verzi, teď používaly novou verzi. Chcete-li určit, zda se má použít zásada vydavatele pro konkrétní sestavení, vložte **> prvek\<publisherPolicy** do **\<dependentAssembly >** .  
  
 Výchozí nastavení atributu **Apply** je **Ano**. Nastavení atributu **Apply** na hodnotu **ne** přepíše všechna předchozí nastavení **Ano** pro sestavení.  
  
 Aby aplikace explicitně ignorovala zásady vydavatele pomocí [\<publisherPolicy Apply = "No"/>](publisherpolicy-element.md) v konfiguračním souboru aplikace, vyžaduje oprávnění. Oprávnění je uděleno nastavením příznaku <xref:System.Security.Permissions.SecurityPermissionFlag> na <xref:System.Security.Permissions.SecurityPermission>. Další informace naleznete v tématu [oprávnění zabezpečení přesměrování vazby sestavení](../../assembly-binding-redirection-security-permission.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vypne zásady vydavatele pro sestavení `myAssembly`.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Jak běhové prostředí vyhledává sestavení](../../../deployment/how-the-runtime-locates-assemblies.md)
- [Přesměrování verzí sestavení](../../redirect-assembly-versions.md)
