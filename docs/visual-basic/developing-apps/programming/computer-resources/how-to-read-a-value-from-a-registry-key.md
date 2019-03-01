---
title: 'Postupy: Načtení hodnoty z klíče registru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: 35fa839f80f422f334e96d7c5bf0bbd5f12484ad
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966928"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Postupy: Načtení hodnoty z klíče registru v jazyce Visual Basic
`GetValue` Metodu `My.Computer.Registry` objekt lze použít ke čtení hodnoty registru Windows.  
  
 Pokud není k dispozici klíč "Software\MyApp" v následujícím příkladu, je vyvolána výjimka. Pokud `ValueName`, "Název" v následujícím příkladu, neexistuje, `Nothing` je vrácena.  
  
 `GetValue` Metoda slouží také k určení, zda daná hodnota existuje v klíči registru.  
  
 Když kód čte registru z webové aplikace, je aktuální uživatel je vzhledem k ověřování a zosobnění, která je implementována ve webové aplikaci.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>K načtení hodnoty z klíče registru  
  
-   Použít `GetValue` metoda zadáním cesty a názvu) k načtení hodnoty z klíče registru. Následující příklad přečte hodnotu `Name` z `HKEY_CURRENT_USER\Software\MyApp` a zobrazí jej v okně se zprávou.  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu je umístěn v **operačního systému Windows > registru**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>Chcete-li zjistit, zda je hodnota v klíči registru existuje  
  
-   Použití `GetValue` metody k načtení hodnoty. Následující kód ověří, zda hodnota existuje a vrátí zprávu, pokud tomu tak není.  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Registr obsahuje nejvyšší úrovně a kořenové klíče, které se používají k ukládání dat. Například HKEY_LOCAL_MACHINE kořenový klíč se používá pro ukládání nastavení na úrovni počítače používané všichni uživatelé, i když HKEY_CURRENT_USER slouží k ukládání dat specifických pro jednotlivé uživatele.  
  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název klíče je `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Uživatel nemá oprávnění ke čtení z klíče registru (<xref:System.Security.SecurityException>).  
  
-   Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pokud chcete spustit tento proces, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.RegistryPermission> třídy. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku, protože nedostatečná oprávnění. Podobně uživatel musí mít správné seznamy ACL pro vytvoření nebo zápis do nastavení. Místní aplikace, který má oprávnění zabezpečení přístupu kódu například nemusí mít oprávnění operačního systému. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
