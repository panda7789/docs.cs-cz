---
title: Zabezpečení a registr
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 454180207d6432e80d87941d1f329f2a4ea7a801
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345484"
---
# <a name="security-and-the-registry-visual-basic"></a>Zabezpečení a registr (Visual Basic)

Tato stránka popisuje důsledky zabezpečení ukládání dat do registru.  
  
## <a name="permissions"></a>Oprávnění  

 Není bezpečné ukládat tajné klíče, jako jsou hesla, v registru jako prostý text, a to i v případě, že je klíč registru chráněný pomocí seznamů řízení přístupu (ACL).  
  
 Práce s registrem může ohrozit zabezpečení tím, že umožňuje nevhodný přístup k systémovým prostředkům nebo chráněným informacím. Chcete-li použít tyto vlastnosti, musíte mít oprávnění ke čtení a zápisu z výčtu <xref:System.Security.Permissions.RegistryPermissionAccess>, který řídí přístup k proměnným registru. Veškerý kód spuštěný s úplným vztahem důvěryhodnosti (pod výchozí zásadou zabezpečení je to jakýkoli kód nainstalovaný na místním pevném disku uživatele) má potřebná oprávnění pro přístup k registru. Další informace naleznete v tématu <xref:System.Security.Permissions.RegistryPermission> Class.  
  
 Proměnné registru by neměly být uloženy v umístěních paměti, kde k nim má přístup kód bez <xref:System.Security.Permissions.RegistryPermission>. Podobně při udělování oprávnění udělte minimální oprávnění potřebná k provedení úlohy.  
  
 Hodnoty přístupu k oprávněním registru jsou definovány výčtem <xref:System.Security.Permissions.RegistryPermissionAccess>. Následující tabulka podrobně popisuje její členy.  
  
|Hodnota|Přístup k proměnným registru|  
|-----------|----------------------------------|  
|`AllAccess`|Vytváření, čtení a zápis|  
|`Create`|Create|  
|`NoAccess`|Bez přístupu|  
|`Read`|Pro čtení|  
|`Write`|Zapisovat|  
  
## <a name="checking-values-in-registry-keys"></a>Kontrola hodnot v klíčích registru  

 Když vytváříte hodnotu registru, musíte se rozhodnout, co dělat, pokud tato hodnota již existuje. Jiný proces, pravděpodobně škodlivý, již mohl vytvořit hodnotu a mít k ní přístup. Při vložení dat do hodnoty registru jsou data k dispozici pro druhý proces. Chcete-li tomu zabránit, použijte metodu `GetValue`. Vrátí `Nothing`, pokud klíč ještě neexistuje.  
  
> [!IMPORTANT]
> Při čtení registru z webové aplikace závisí identita aktuálního uživatele na ověřování a zosobnění implementovaného ve webové aplikaci.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
