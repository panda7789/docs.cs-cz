---
title: 'Postupy: Načtení hodnoty z klíče registru'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: 73c32aefe06a68bb42fcb5f4615da0927e57e892
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345605"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Postupy: Načtení hodnoty z klíče registru v jazyce Visual Basic

Metodu `GetValue` objektu `My.Computer.Registry` lze použít ke čtení hodnot v registru systému Windows.  
  
 Pokud klíč "Software\MyApp" v následujícím příkladu neexistuje, je vyvolána výjimka. Pokud `ValueName`, "Název" v následujícím příkladu `Nothing` neexistuje, je vrácena.  
  
 Metodu `GetValue` lze také použít k určení, zda daná hodnota existuje v určitém klíči registru.  
  
 Při čtení kódu z webové aplikace je aktuální uživatel určen ověřováním a zosobněním, které je implementováno ve webové aplikaci.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>Čtení hodnoty z klíče registru  
  
- Pomocí `GetValue` metody určující cestu a název) přečtete hodnotu z klíče registru. Následující příklad přečte `Name` `HKEY_CURRENT_USER\Software\MyApp` hodnotu z a zobrazí ji v poli se zprávou.  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu IntelliSense. Ve výběru fragmentu kódu je umístěn v registru **operačního systému Windows >**. Další informace naleznete v [tématu Fragmenty kódu](/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>Chcete-li zjistit, zda hodnota existuje v klíči registru  
  
- Pomocí `GetValue` metody načtěte hodnotu. Následující kód zkontroluje, zda hodnota existuje, a vrátí zprávu, pokud tomu tak není.  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Registr obsahuje klíče nejvyšší úrovně nebo root, které se používají k ukládání dat. Například kořenový klíč HKEY_LOCAL_MACHINE se používá pro ukládání nastavení na úrovni počítače používané všemi uživateli, zatímco HKEY_CURRENT_USER se používá pro ukládání dat specifických pro jednotlivé uživatele.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Název klíče je `Nothing` (<xref:System.ArgumentNullException>).  
  
- Uživatel nemá oprávnění ke čtení z<xref:System.Security.SecurityException>klíčů registru ( ).  
  
- Název klíče překračuje limit 255 znaků<xref:System.ArgumentException>( ).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 Chcete-li spustit tento proces, vaše sestavení <xref:System.Security.Permissions.RegistryPermission> vyžaduje úroveň oprávnění udělené třídou. Pokud jsou spuštěny v kontextu částečné důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění. Podobně musí mít uživatel správné akly pro vytváření nebo zápis do nastavení. Například místní aplikace, která má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému. Další informace naleznete v [tématu Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
