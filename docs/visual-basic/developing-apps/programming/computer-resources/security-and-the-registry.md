---
title: Zabezpečení a registr (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: dc0071d1fddf99bd712ebe8aea5c61bbc3522f93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921209"
---
# <a name="security-and-the-registry-visual-basic"></a>Zabezpečení a registr (Visual Basic)
Tato stránka pojednává o bezpečnostních důsledcích ukládání dat do registru.  
  
## <a name="permissions"></a>Oprávnění  
 Není bezpečné uchovávat tajemství, jako jsou hesla, v registrech jako prostý text, i v případě, že klíč registru je chráněn pomocí ACL (seznamy řízení přístupu).  
  
 Práce s registrem může ohrozit zabezpečení tím, že nevhodný přístup k systémovým prostředkům nebo chráněné informace. Použití těchto vlastností, musíte mít oprávnění z čtení a zápisu <xref:System.Security.Permissions.RegistryPermissionAccess> výčtu, které řídí přístup k proměnné registru. Jakýkoli kód spuštěn s úplným vztahem důvěryhodnosti (podle výchozí zásady zabezpečení, je to žádný kód nainstalované na místním pevném disku uživatele) má potřebná oprávnění pro přístup k registru. Další informace najdete v tématu <xref:System.Security.Permissions.RegistryPermission> třídy.  
  
 Proměnné registru by neměly být uloženy v umístění v paměti kde kódu bez <xref:System.Security.Permissions.RegistryPermission> k nim přistupovat. Podobně při udělování oprávnění udělte minimální oprávnění, které jsou nezbytné k dokončení práce.  
  
 Oprávnění k registrům, jsou určené <xref:System.Security.Permissions.RegistryPermissionAccess> výčtu. Následující tabulka obsahuje podrobnosti o jejích členů.  
  
|Hodnota|Přístup k proměnné registru|  
|-----------|----------------------------------|  
|`AllAccess`|Vytvoření, čtení a zápis|  
|`Create`|Create|  
|`NoAccess`|Žádný přístup|  
|`Read`|Číst|  
|`Write`|Write|  
  
## <a name="checking-values-in-registry-keys"></a>Kontroluje se hodnoty klíče registru  
 Když vytváříte hodnotu registru, musíte se rozhodnout, co dělat, pokud tuto hodnotu již existuje. Jiný proces, možná škodlivý ten už možná máte vytvořené hodnotu a k ní máte přístup. Když vkládáte data do hodnoty registru, data jsou k dispozici pro jiné procesy. Chcete-li tomu zabránit, použijte `GetValue` metody. Vrátí `Nothing` Pokud klíč ještě neexistuje.  
  
> [!IMPORTANT]
>  Při čtení registru z webové aplikace, identity aktuálního uživatele závisí na ověřování a zosobnění implementované ve webové aplikaci.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
