---
title: Zabezpečení a registr
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 2eba9d177769b22de3f931bc7af4905a80e316b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359965"
---
# <a name="security-and-the-registry-visual-basic"></a>Zabezpečení a registr (Visual Basic)

Tato stránka popisuje důsledky zabezpečení ukládání dat do registru.  
  
## <a name="permissions"></a>Oprávnění  

 Není bezpečné ukládat tajné klíče, jako jsou hesla, v registru jako prostý text, a to i v případě, že je klíč registru chráněný pomocí seznamů řízení přístupu (ACL).  
  
 Práce s registrem může ohrozit zabezpečení tím, že umožňuje nevhodný přístup k systémovým prostředkům nebo chráněným informacím. Chcete-li použít tyto vlastnosti, musíte mít oprávnění ke čtení a zápisu z <xref:System.Security.Permissions.RegistryPermissionAccess> výčtu, který řídí přístup k proměnným registru. Veškerý kód spuštěný s úplným vztahem důvěryhodnosti (pod výchozí zásadou zabezpečení je to jakýkoli kód nainstalovaný na místním pevném disku uživatele) má potřebná oprávnění pro přístup k registru. Další informace naleznete v tématu <xref:System.Security.Permissions.RegistryPermission> Třída.  
  
 Proměnné registru by neměly být uloženy v umístěních paměti, kde kód bez <xref:System.Security.Permissions.RegistryPermission> přístupu k nim mají přístup. Podobně při udělování oprávnění udělte minimální oprávnění potřebná k provedení úlohy.  
  
 Hodnoty přístupu k oprávněním registru jsou definovány <xref:System.Security.Permissions.RegistryPermissionAccess> výčtem. Následující tabulka podrobně popisuje její členy.  
  
|Hodnota|Přístup k proměnným registru|  
|-----------|----------------------------------|  
|`AllAccess`|Vytváření, čtení a zápis|  
|`Create`|Vytvořit|  
|`NoAccess`|Bez přístupu|  
|`Read`|Čtení|  
|`Write`|Zápis|  
  
## <a name="checking-values-in-registry-keys"></a>Kontrola hodnot v klíčích registru  

 Když vytváříte hodnotu registru, musíte se rozhodnout, co dělat, pokud tato hodnota již existuje. Jiný proces, pravděpodobně škodlivý, již mohl vytvořit hodnotu a mít k ní přístup. Při vložení dat do hodnoty registru jsou data k dispozici pro druhý proces. Chcete-li tomu zabránit, použijte `GetValue` metodu. Vrátí, `Nothing` Pokud klíč ještě neexistuje.  
  
> [!IMPORTANT]
> Při čtení registru z webové aplikace závisí identita aktuálního uživatele na ověřování a zosobnění implementovaného ve webové aplikaci.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Čtení z registru a zápis do něj](reading-from-and-writing-to-the-registry.md)
