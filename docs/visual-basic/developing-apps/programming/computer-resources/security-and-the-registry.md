---
title: Zabezpečení a registr (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: ddfe8f88763ee2db78d25d72e6c9cb3456ccd13f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583926"
---
# <a name="security-and-the-registry-visual-basic"></a>Zabezpečení a registr (Visual Basic)
Tato stránka popisuje bezpečnostních důsledcích ukládání dat v registru.  
  
## <a name="permissions"></a>Oprávnění  
 Není bezpečné uchovávat tajné údaje, jako jsou hesla, v registru jako prostý text, i v případě, že je klíč registru chráněn pomocí seznamů řízení přístupu (seznamy řízení přístupu).  
  
 Práce s registrem může ohrozit zabezpečení tím, že nevhodný přístup k systémovým prostředkům nebo chráněný informace. Pokud chcete použít tyto vlastnosti, musí mít oprávnění z čtení a zápisu <xref:System.Security.Permissions.RegistryPermissionAccess> výčtu, která řídí přístup k registru proměnné. Jakýkoli kód spuštěn s úplným vztahem důvěryhodnosti (v části výchozí zásady zabezpečení, je to žádný kód nainstalována na místní pevný disk uživatele) musí mít potřebná oprávnění pro přístup k registru. Další informace najdete v tématu <xref:System.Security.Permissions.RegistryPermission> třídy.  
  
 Proměnné registru by neměly být uloženy v umístění v paměti kde code bez <xref:System.Security.Permissions.RegistryPermission> k nim měli přístup. Podobně při udělování oprávnění, udělte minimální oprávnění potřebná k provedení úlohy.  
  
 Oprávnění k registrům jsou definovány <xref:System.Security.Permissions.RegistryPermissionAccess> výčtu. Následující tabulka uvádí její členy.  
  
|Hodnota|Přístup k registru proměnné|  
|-----------|----------------------------------|  
|`AllAccess`|Vytváření, čtení a zápis|  
|`Create`|Create|  
|`NoAccess`|Žádný přístup|  
|`Read`|Číst|  
|`Write`|Write|  
  
## <a name="checking-values-in-registry-keys"></a>Kontrola hodnoty klíče registru  
 Když vytvoříte hodnotu registru, budete muset rozhodnout, co dělat v případě, že hodnota již existuje. Jiný proces, případně škodlivý jeden už možná máte vytvořené hodnota a mít přístup k němu. Když vložíte dat v hodnotě registru, data jsou k dispozici pro jiný proces. Chcete-li tomu zabránit, použijte `GetValue` metoda. Vrátí `Nothing` Pokud klíč ještě neexistuje.  
  
> [!IMPORTANT]
>  Při čtení registru z webové aplikace, identity aktuální uživatel závisí na ověřování a zosobnění implementována ve webové aplikaci.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
