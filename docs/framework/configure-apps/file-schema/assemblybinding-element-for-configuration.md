---
title: '&lt;assemblybinding –&gt; – element pro &lt;konfigurace&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 5693b92ac35a357ff1f8643d0eb9ec2105acecb4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073460"
---
# <a name="assemblybinding-element-for-configuration"></a>\<assemblybinding – > – element pro \<configuration >

Určuje zásady vazeb sestavení na úrovni konfigurace.

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
| **xmlns.** | Požadovaný atribut.<br><br>Určuje obor názvů XML, vyžaduje se pro vazby sestavení. Použijte řetězec "urn: schémata-microsoft-com:asm.v1" jako hodnotu. |

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-element"></a>Podřízený element.

|     | Popis |
| --- | ----------- |
| [**\<linkedconfiguration – >**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | Určuje konfigurační soubor, který chcete zahrnout. |

## <a name="remarks"></a>Poznámky

[  **\<Linkedconfiguration – >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element zjednodušuje správu sestavení komponent tím, že konfigurační soubory v konfiguračních souborech aplikace, které chcete zahrnout sestavení dobře známé umístění, spíše než duplikace nastavení konfigurace sestavení.

> [!NOTE]
> **\<Linkedconfiguration – >** element není podporován pro aplikace s Windows manifesty vedle sebe.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zahrnout konfigurační soubor na místním pevném disku:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Viz také:

[Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
