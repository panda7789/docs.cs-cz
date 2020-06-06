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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155476"
---
# <a name="assemblybinding-element-for-configuration"></a>\<assemblyBinding> – element pro \<configuration>

Určuje zásadu vazby sestavení na úrovni konfigurace.

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**

## <a name="syntax"></a>Syntaxe

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **xmlns** | Požadovaný atribut.<br><br>Určuje obor názvů XML vyžadovaný pro vazbu sestavení. Jako hodnotu použijte řetězec "urn: schemas-microsoft-com: asm. v1". |

## <a name="parent-element"></a>Nadřazený element

|     | Description |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-element"></a>Podřízený element

|     | Description |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | Určuje konfigurační soubor, který se má zahrnout. |

## <a name="remarks"></a>Poznámky

[**\<linkedConfiguration>**](linkedconfiguration-element.md)Prvek zjednodušuje správu sestavení komponent tím, že umožňuje souborům konfigurace aplikace zahrnout konfigurační soubory sestavení do dobře známých umístění, nikoli duplikovat nastavení konfigurace sestavení.

> [!NOTE]
> **\<linkedConfiguration>** Element není podporován pro aplikace s manifesty vedle sebe v systému Windows.

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

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
