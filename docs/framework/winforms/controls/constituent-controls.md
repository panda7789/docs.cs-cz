---
title: Základní ovládací prvky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
ms.openlocfilehash: 522a1012fc7bdd54860b0538064ee073f7a761f7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918430"
---
# <a name="constituent-controls"></a>Základní ovládací prvky
Ovládací prvky, které tvoří uživatelský ovládací prvek nebo *ovládací prvky prvku* , když jsou vyvolány, jsou relativně neflexibilní, pokud jsou k dispozici pro vlastní vykreslování grafiky. Všechny model Windows Forms ovládací prvky zpracovávají své vlastní vykreslení prostřednictvím své <xref:System.Windows.Forms.Control.OnPaint%2A> vlastní metody. Vzhledem k tomu, že je tato metoda chráněná, není vývojářům přístupná, takže se nedá zabránit ve spuštění, když je ovládací prvek vykreslený. To však neznamená, že nemůžete přidat kód, který by ovlivnil vzhled prvků prvku. Další vykreslování lze provést přidáním obslužné rutiny události. Předpokládejme například, že jste provedli <xref:System.Windows.Forms.UserControl> vytváření pomocí tlačítka s `MyButton`názvem. Pokud chcete mít další vykreslování nad rámec toho <xref:System.Web.UI.WebControls.Button>, co bylo poskytnuto, měli byste přidat kód do uživatelského ovládacího prvku, který bude vypadat přibližně takto:  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=   
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,   
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
> Některé ovládací prvky model Windows Forms, například <xref:System.Windows.Forms.TextBox>, jsou vykresleny přímo v systému Windows. V těchto instancích <xref:System.Windows.Forms.Control.OnPaint%2A> není metoda nikdy volána, takže výše uvedený příklad nebude nikdy volán.  
  
 Tím se vytvoří metoda, která se spustí pokaždé, když se `MyButton.Paint` událost spustí, a přidá další grafické znázornění ovládacího prvku. Všimněte si, že to nebrání spuštění `MyButton.OnPaint`, a proto veškeré vykreslování obvykle prováděné tlačítkem bude i nadále provedeno kromě vlastního malování. Podrobnosti o technologii rozhraní GDI+ a vlastním vykreslování naleznete v tématu [vytváření grafických imagí s rozhraním GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md). Pokud chcete mít jedinečný reprezentace vašeho ovládacího prvku, je nejlepší postup vytvořit Zděděný ovládací prvek a napsat pro něj vlastní kód pro vykreslování. Podrobnosti najdete v tématu [ovládací prvky vykreslené uživatelem](user-drawn-controls.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Ovládací prvky vykreslované uživatelem](user-drawn-controls.md)
- [Postupy: Vytvoření grafických objektů pro kreslení](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
