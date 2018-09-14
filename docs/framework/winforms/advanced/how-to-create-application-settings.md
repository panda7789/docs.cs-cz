---
title: 'Postupy: Vytváření nastavení aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
ms.openlocfilehash: 7a84fc85b42f2b78ccafcae3c815847633b9916d
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45508041"
---
# <a name="how-to-create-application-settings"></a>Postupy: Vytváření nastavení aplikace
Pomocí spravovaného kódu, můžete vytvořit nové nastavení aplikace a svázat ho s vlastnostmi na formulář nebo ovládací prvky do formuláře, takže tato nastavení jsou načtena a za běhu automaticky uloženy.  
  
 V následujícím postupu vytvoříte ručně obálkovou třídu, která je odvozena z <xref:System.Configuration.ApplicationSettingsBase>. Do této třídy přidat vlastnost veřejně přístupné pro každé nastavení aplikace, kterou chcete zveřejnit.  
  
 Můžete také provést tento postup pomocí minimálního psaní kódu v návrháři aplikace Visual Studio.  Viz také [postupy: vytvoření aplikace nastavení pomocí návrháře](https://msdn.microsoft.com/library/wabtadw6\(v=vs.110\)).  
  
### <a name="to-create-new-application-settings-programmatically"></a>Chcete-li vytvořit nové nastavení aplikace prostřednictvím kódu programu  
  
1.  Přidejte novou třídu do projektu a přejmenujte jej. V tomto postupu budeme volat tuto třídu `MyUserSettings`. Změnit definici třídy, takže je odvozena z třídy <xref:System.Configuration.ApplicationSettingsBase>.  
  
2.  Definovat vlastnost na této obálkové třídy pro každé nastavení aplikace, budete potřebovat a použít tuto vlastnost buď <xref:System.Configuration.ApplicationScopedSettingAttribute> nebo <xref:System.Configuration.UserScopedSettingAttribute>, v závislosti na rozsahu nastavení. Další informace o nastavení oboru, naleznete v tématu [přehled nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-overview.md). Nyní váš kód by měl vypadat takto:  
  
     [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  Vytvoření instance této obálkové třídy ve vaší aplikaci. Běžně je soukromý člen hlavního formuláře. Teď, když jste definovali vaší třídy, je potřeba ho vytvořit vazbu na vlastnost; v takovém případě <xref:System.Windows.Forms.Form.BackColor%2A> vlastnost formuláře. Můžete to udělat v formuláře `Load` obslužné rutiny události.  
  
     [!code-csharp[ApplicationSettings.Create#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  Pokud zadáte způsob, jak změnit nastavení v době běhu, je potřeba uložit aktuální nastavení uživatele na disk, když se zavře formulář, jinak tyto změny budou ztraceny.  
  
     [!code-csharp[ApplicationSettings.Create#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     Jste teď úspěšně vytvořili nové nastavení aplikace a vázán na zadanou vlastnost.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Ve výchozím nastavení <xref:System.Configuration.LocalFileSettingsProvider>, opakuje informace ke konfiguračním souborům jako prostý text. Toto omezení zabezpečení k zabezpečení přístupu k souboru v operačním systému k dispozici pro aktuálního uživatele. Z tohoto důvodu musíte věnovat pozornost s informacemi uloženými v konfiguračních souborech. Jeden běžně používá pro nastavení aplikace je například ukládání připojovacích řetězců, které odkazují na úložiště dat aplikace. Kvůli zajištění zabezpečení, ale tyto řetězce by neměl obsahovat hesla. Další informace o připojovacích řetězcích najdete v tématu <xref:System.Configuration.SpecialSetting>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Configuration.SpecialSettingAttribute>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 [Přehled nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [Postupy: Ověření nastavení aplikace](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)
