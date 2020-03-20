---
title: <assemblyBinding> – element pro <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 21cf5e749b0dae310c3326f8abf82c6678fc97e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155476"
---
# <a name="assemblybinding-element-for-configuration"></a>\<assemblyBinding> \<element pro konfigurační>

Určuje zásadu vazby sestavení na úrovni konfigurace.

konfigurace &nbsp; &nbsp;>[** \<**](configuration-element.md) **>\<vazby sestavení**

## <a name="syntax"></a>Syntaxe

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **Xmlns** | Požadovaný atribut.<br><br>Určuje obor názvů XML požadovaný pro vazbu sestavení. Jako hodnotu použijte řetězec "urn:schemas-microsoft-com:asm.v1". |

## <a name="parent-element"></a>Nadřazený prvek

|     | Popis |
| --- | ----------- |
| [**\<>konfigurace**](configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-element"></a>Podřízený prvek

|     | Popis |
| --- | ----------- |
| [**\<linkedKonfigurační>**](linkedconfiguration-element.md) | Určuje konfigurační soubor, který má být zahrnut. |

## <a name="remarks"></a>Poznámky

Prvek [** \<LinkedConfiguration>**](linkedconfiguration-element.md) zjednodušuje správu sestav součástí tím, že umožňuje konfiguračním souborům aplikací zahrnout konfigurační soubory sestavení do známých umístění, nikoli duplikovat nastavení konfigurace sestavení.

> [!NOTE]
> Prvek ** \<linkedConfiguration>** není podporován pro aplikace s windows side-by-side manifesty.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zahrnout konfigurační soubor na místní pevný disk:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru pro rozhraní .NET Framework](index.md)
