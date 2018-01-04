---
title: "&lt;assemblybinding –&gt; element pro &lt;konfigurace&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8d670c56a885a5fdae059a87f63fba9ab32f020c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="assemblybinding-element-for-configuration"></a>\<assemblybinding – > elementu pro \<konfigurace >

Určuje sestavení vazby zásady na úrovni konfigurace.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<assemblybinding – >**

## <a name="syntax"></a>Syntaxe

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **atribut xmlns** | Požadovaný atribut.<br><br>Určuje obor názvů XML, které jsou potřebné pro sestavení – vazby. Použít řetězec "urn: schémata-microsoft-com:asm.v1" jako hodnotu. |

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-element"></a>Podřízený element

|     | Popis |
| --- | ----------- |
| [**\<linkedconfiguration – >**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | Určuje konfigurační soubor pro zahrnout. |

## <a name="remarks"></a>Poznámky

[  **\<Linkedconfiguration – >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element zjednodušuje správu sestavení součástí tím, že konfigurační soubory v konfigurační soubory aplikace zahrnete sestavení dobře známé umístění, a nikoli duplicitní nastavení konfigurace sestavení.

> [!NOTE]
>  **\<Linkedconfiguration – >** element není podporován pro aplikace s manifesty Windows vedle sebe.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak chcete zahrnout konfigurační soubor na místní pevný disk:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Viz také

[Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
