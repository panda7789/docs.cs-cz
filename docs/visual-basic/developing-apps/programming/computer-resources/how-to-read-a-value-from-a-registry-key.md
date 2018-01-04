---
title: "Postupy: Načtení hodnoty z klíče registru v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4aa939d7b2d89bd878705ac67f2b6f37838f6ea2
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Postupy: Načtení hodnoty z klíče registru v jazyce Visual Basic
`GetValue` Metodu `My.Computer.Registry` objekt můžete použít ke čtení hodnoty v registru systému Windows.  
  
 Pokud není k dispozici klíč, "Software\MyApp" v následujícím příkladu, je vyvolána výjimka. Pokud `ValueName`, "Název" v následujícím příkladu neexistuje, `Nothing` je vrácen.  
  
 `GetValue` Metoda slouží také k určení, zda daná hodnota existuje v klíči registru.  
  
 Když kód čte registru z webové aplikace, je aktuální uživatel je dáno ověřování a zosobnění, která je implementována ve webové aplikaci.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>K načtení hodnoty z klíče registru  
  
-   Použít `GetValue` metoda, zadáte cestu a název) k načtení hodnoty z klíče registru. Následující příklad načte hodnotu `Name` z `HKEY_CURRENT_USER\Software\MyApp` a zobrazí v okně se zprávou.  
  
     [!code-vb[VbResourceTasks#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_1.vb)]  
  
 Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu. V Sběrač fragmentů kódu je umístěn v **operačního systému Windows > registru**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>K určení, zda hodnota existuje v klíči registru  
  
-   Použití `GetValue` metodu k získání hodnoty. Následující kód ověří, zda hodnota existuje a vrátí zprávu, pokud neexistuje.  
  
     [!code-vb[VbResourceTasks#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_2.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Registr obsahuje nejvyšší úrovně nebo kořenové klíče, které se používají k ukládání dat. Například HKEY_LOCAL_MACHINE kořenový klíč se používá pro ukládání nastavení používané všechny uživatele, i když HKEY_CURRENT_USER se používá pro ukládání dat, které jsou specifické pro jednotlivé uživatele.  
  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název klíče je `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Uživatel nemá oprávnění ke čtení z klíče registru (<xref:System.Security.SecurityException>).  
  
-   Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pokud chcete spustit tento proces, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.RegistryPermission> třídy. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění. Podobně uživatel musí mít správné seznamy řízení přístupu pro vytvoření nebo zápis k nastavení. Například místní aplikace, který má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.Win32.RegistryHive>  
 [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
