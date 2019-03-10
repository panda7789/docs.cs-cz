---
title: 'Postupy: Vytvořit nastavení aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
ms.openlocfilehash: d540715c0b4c69b2981cc65f55b0fa950c5a4eaf
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721239"
---
# <a name="how-to-create-application-settings"></a>Postupy: Vytvořit nastavení aplikace
Pomocí spravovaného kódu, můžete vytvořit nové nastavení aplikace a svázat ho s vlastnostmi na formulář nebo ovládací prvky do formuláře, takže tato nastavení jsou načtena a za běhu automaticky uloženy.  
  
 V následujícím postupu vytvoříte ručně obálkovou třídu, která je odvozena z <xref:System.Configuration.ApplicationSettingsBase>. Do této třídy přidat vlastnost veřejně přístupné pro každé nastavení aplikace, kterou chcete zveřejnit.  
  
 Můžete také provést tento postup pomocí minimálního psaní kódu v návrháři aplikace Visual Studio.  Viz také [jak: Vytvořit nastavení aplikace pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100)).  
  
### <a name="to-create-new-application-settings-programmatically"></a>Chcete-li vytvořit nové nastavení aplikace prostřednictvím kódu programu  
  
1.  Přidejte novou třídu do projektu a přejmenujte jej. V tomto postupu budeme volat tuto třídu `MyUserSettings`. Změnit definici třídy, takže je odvozena z třídy <xref:System.Configuration.ApplicationSettingsBase>.  
  
2.  Definovat vlastnost na této obálkové třídy pro každé nastavení aplikace, budete potřebovat a použít tuto vlastnost buď <xref:System.Configuration.ApplicationScopedSettingAttribute> nebo <xref:System.Configuration.UserScopedSettingAttribute>, v závislosti na rozsahu nastavení. Další informace o nastavení oboru, naleznete v tématu [přehled nastavení aplikace](application-settings-overview.md). Nyní váš kód by měl vypadat takto:  
  
     [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  Vytvoření instance této obálkové třídy ve vaší aplikaci. Běžně je soukromý člen hlavního formuláře. Teď, když jste definovali vaší třídy, je potřeba ho vytvořit vazbu na vlastnost; v takovém případě <xref:System.Windows.Forms.Form.BackColor%2A> vlastnost formuláře. Můžete to udělat v formuláře `Load` obslužné rutiny události.  
  
     [!code-csharp[ApplicationSettings.Create#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  Pokud zadáte způsob, jak změnit nastavení v době běhu, je potřeba uložit aktuální nastavení uživatele na disk, když se zavře formulář, jinak tyto změny budou ztraceny.  
  
     [!code-csharp[ApplicationSettings.Create#3](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     Jste teď úspěšně vytvořili nové nastavení aplikace a vázán na zadanou vlastnost.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Ve výchozím nastavení <xref:System.Configuration.LocalFileSettingsProvider>, opakuje informace ke konfiguračním souborům jako prostý text. Toto omezení zabezpečení k zabezpečení přístupu k souboru v operačním systému k dispozici pro aktuálního uživatele. Z tohoto důvodu musíte věnovat pozornost s informacemi uloženými v konfiguračních souborech. Jeden běžně používá pro nastavení aplikace je například ukládání připojovacích řetězců, které odkazují na úložiště dat aplikace. Kvůli zajištění zabezpečení, ale tyto řetězce by neměl obsahovat hesla. Další informace o připojovacích řetězcích najdete v tématu <xref:System.Configuration.SpecialSetting>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Configuration.SpecialSettingAttribute>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Přehled nastavení aplikace](application-settings-overview.md)
- [Postupy: Ověření nastavení aplikace](how-to-validate-application-settings.md)
