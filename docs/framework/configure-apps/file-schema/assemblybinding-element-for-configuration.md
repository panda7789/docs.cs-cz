---
title: <assemblyBinding> – element pro <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: e0b83c4b3573ab6819654e72cac1bf3e4a0ba637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921276"
---
# <a name="assemblybinding-element-for-configuration"></a>\<assemblyBinding element > pro \<konfigurační >

Určuje zásadu vazby sestavení na úrovni konfigurace.

[ **\<> Konfigurace**](configuration-element.md)   
&nbsp;&nbsp; **\<assemblyBinding >**

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

|     | Popis |
| --- | ----------- |
| [ **\<> Konfigurace**](configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-element"></a>Podřízený element

|     | Popis |
| --- | ----------- |
| [ **\<linkedConfiguration>** ](linkedconfiguration-element.md) | Určuje konfigurační soubor, který se má zahrnout. |

## <a name="remarks"></a>Poznámky

Element [**linkedConfiguration > zjednodušuje správu sestavení komponent tím, že umožňuje aplikačním konfiguračním souborům zahrnout konfigurační soubory sestavení do známých umístění místo duplikace sestavení. \<** ](linkedconfiguration-element.md) nastavení konfigurace.

> [!NOTE]
> **\<Linkedconfiguration – >** element není podporován pro aplikace s Windows manifesty vedle sebe.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zahrnout konfigurační soubor na místní pevný disk:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
