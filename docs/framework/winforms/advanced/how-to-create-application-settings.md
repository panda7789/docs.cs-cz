---
title: "Postupy: Vytváření nastavení aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 481239b472ced5ef6251b665dad16e83a170607d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-application-settings"></a>Postupy: Vytváření nastavení aplikace
Pomocí spravovaného kódu, můžete vytvořit nové nastavení aplikace a navázat je na vlastnosti svého formuláře nebo svého formuláře ovládací prvky, tak, aby tato nastavení jsou načteny a automaticky uloženy v době běhu.  
  
 V následujícím postupu vytvoříte ručně obálkovou třídu odvozenou od <xref:System.Configuration.ApplicationSettingsBase>. Pro tuto třídu přidáte veřejně přístupná vlastnost pro každé nastavení aplikace, kterou chcete vystavit.  
  
 Tento postup pomocí minimální kódu v návrháři Visual Studio můžete také provést.  Viz také [postupy: vytvoření aplikace nastavení pomocí návrháře](http://msdn.microsoft.com/library/wabtadw6\(v=vs.110\)).  
  
### <a name="to-create-new-application-settings-programmatically"></a>Chcete-li vytvořit nové nastavení aplikace prostřednictvím kódu programu  
  
1.  Přidejte novou třídu do projektu a přejmenujte ji. Pro tento postup jsme zavolá Tato třída `MyUserSettings`. Změňte definici třídy tak, aby třída odvozená z <xref:System.Configuration.ApplicationSettingsBase>.  
  
2.  Definujte vlastnost této obálkové třídy pro každé nastavení aplikace, budete potřebovat a použít tuto vlastnost se buď <xref:System.Configuration.ApplicationScopedSettingAttribute> nebo <xref:System.Configuration.UserScopedSettingAttribute>, v závislosti na rozsahu nastavení. Další informace o nastavení oboru, najdete v části [přehled nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-overview.md). Nyní by váš kód by měl vypadat takto:  
  
     [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  Vytvoření instance této třídy obálku ve vaší aplikaci. Obvykle bude členem privátní hlavní formulář. Teď, když jste definovali třídě, musíte pro vytvoření vazby na vlastnost; v takovém případě <xref:System.Windows.Forms.Form.BackColor%2A> vlastnosti svého formuláře. Můžete to provést v svého formuláře `Load` obslužné rutiny události.  
  
     [!code-csharp[ApplicationSettings.Create#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  Pokud zadáte způsob, jak změnit nastavení v době běhu, musíte uložit aktuální nastavení uživatele na disk, když svého formuláře zavře, jinak tyto změny budou ztraceny.  
  
     [!code-csharp[ApplicationSettings.Create#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     Teď úspěšně vytvořit nové nastavení aplikace a vázána na zadanou vlastnost.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Ve výchozím nastavení <xref:System.Configuration.LocalFileSettingsProvider>, udržuje informace o konfiguračních souborů jako prostý text. Toto omezení zabezpečení zabezpečení přístupu k souboru poskytované operačním systémem pro aktuálního uživatele. Z toho důvodu se musí dát pozor s informacemi uloženými v konfiguračních souborech. Například jeden běžně používá pro nastavení aplikace je k ukládání připojovacích řetězců, které odkazují na úložiště dat aplikace. Z důvodu zabezpečení se ale tyto řetězce by neměla zahrnovat hesla. Další informace o připojovacích řetězcích najdete v tématu <xref:System.Configuration.SpecialSetting>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Configuration.SpecialSettingAttribute>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 [Přehled nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [Postupy: ověření nastavení aplikace](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)
