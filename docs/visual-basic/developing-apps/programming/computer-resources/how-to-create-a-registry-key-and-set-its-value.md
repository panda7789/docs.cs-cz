---
title: 'Postupy: Vytvoření klíče registru a nastavení jeho hodnoty'
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: 459c4b3f971009ee4b6b669c55bc058db0826595
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349203"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>Postupy: Vytvoření klíče registru a nastavení jeho hodnoty v jazyce Visual Basic

Metodu `CreateSubKey` objektu `My.Computer.Registry` lze použít k vytvoření klíče registru.

## <a name="procedure"></a>Postup

### <a name="to-create-a-registry-key"></a>Vytvoření klíče registru

- Použijte `CreateSubKey` metodu určující, podapod pod který podají klíč, a také název klíče. Parametr `Subkey` není rozlišována malá a velká písmena. Tento příklad vytvoří `MyTestKey` klíč registru v části HKEY_CURRENT_USER.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>Vytvoření klíče registru a nastavení hodnoty v něm

1. Použijte `CreateSubkey` metodu určující, podapod pod který podají klíč, a také název klíče. Tento příklad vytvoří `MyTestKey` klíč registru v části HKEY_CURRENT_USER.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. Nastavte hodnotu `SetValue` pomocí metody. Tento příklad nastaví hodnotu řetězce. "MyTestKeyValue" na "Toto je testovací hodnota".

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a>Příklad

Tento příklad vytvoří `MyTestKey` klíč registru pod HKEY_CURRENT_USER `MyTestKeyValue` a `This is a test value`potom nastaví hodnotu řetězce na .

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a>Robustní programování

Zkontrolujte strukturu registru najít vhodné umístění pro váš klíč. Můžete například otevřít klíč HKEY_CURRENT_USER\Software aktuálního uživatele a vytvořit klíč s názvem vaší společnosti. Pak přidejte hodnoty registru do klíče vaší společnosti.

Při čtení registru z webové aplikace závisí aktuální uživatel na ověřování a zosobnění implementovaném ve webové aplikaci.

Je bezpečnější zapisovat data do<xref:Microsoft.Win32.Registry.CurrentUser>uživatelské složky (<xref:Microsoft.Win32.Registry.LocalMachine>) spíše než do místního počítače ( ).

Při vytváření hodnoty registru se musíte rozhodnout, co dělat, pokud tato hodnota již existuje. Jiný proces, možná škodlivý, může mít již vytvořilhodnotu a mají k ní přístup. Když vložíte data do hodnoty registru, data jsou k dispozici pro jiný proces. Chcete-li tomu <xref:Microsoft.Win32.RegistryKey.GetValue%2A> zabránit, použijte metodu. Vrátí, `Nothing` pokud klíč ještě neexistuje.

Není bezpečné ukládat tajné klíče, například hesla, do registru jako prostý text, a to i v případě, že klíč registru je chráněn seznamy ACL (seznamy řízení přístupu).

Následující podmínky mohou způsobit výjimku:

- Název klíče je `Nothing` (<xref:System.ArgumentNullException>).

- Uživatel nemá oprávnění k vytváření klíčů<xref:System.Security.SecurityException>registru ( ).

- Název klíče překračuje limit 255 znaků<xref:System.ArgumentException>( ).

- Klíč je zavřený<xref:System.IO.IOException>( ).

- Klíč registru je jen<xref:System.UnauthorizedAccessException>pro čtení ( ).

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework

Chcete-li spustit tento proces, vaše sestavení <xref:System.Security.Permissions.RegistryPermission> vyžaduje úroveň oprávnění udělené třídou. Pokud jsou spuštěny v kontextu částečné důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění. Podobně musí mít uživatel správné akly pro vytváření nebo zápis do nastavení. Například místní aplikace, která má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému. Další informace naleznete v [tématu Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md)
