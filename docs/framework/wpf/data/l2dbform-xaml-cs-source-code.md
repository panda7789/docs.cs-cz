---
title: Zdrojový kód L2DBForm.xaml.cs
ms.date: 10/22/2019
ms.topic: sample
ms.openlocfilehash: 882699a76eab3c291cd92c298287bc5d28fb08e1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920858"
---
# <a name="l2dbformxamlcs-source-code"></a>Zdrojový kód L2DBForm.xaml.cs

Tato stránka obsahuje obsah a popis C# zdrojového kódu v souboru *L2DBForm.XAML.cs*. Částečná třída L2XDBForm obsažená v tomto souboru může být rozdělena do tří logických částí: datové členy a `OnRemove` a `OnAddBook` kliknutí na tlačítko obslužné rutiny událostí.

## <a name="data-members"></a>Datové členy

K přidružení této třídy k prostředkům okna použitým v souboru *zdrojový kód L2DBForm. XAML*se používají dva soukromé datové členy.

- Proměnná oboru názvů `myBooks` se inicializuje na `"http://www.mybooks.com"`.

- Členský `bookList` je inicializován v konstruktoru do řetězce CDATA v souboru *zdrojový kód L2DBForm. XAML* s následujícím řádkem:

    ```csharp
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
    ```

## <a name="onaddbook-event-handler"></a>Obslužná rutina události OnAddBook

Tato metoda obsahuje následující tři příkazy:

- První podmíněný příkaz se používá pro ověření vstupu.

- Druhý příkaz vytvoří nový <xref:System.Xml.Linq.XElement> z hodnot řetězce, které uživatel zadal v oddílu **Přidat novou knihu** uživatelského rozhraní (UI).

- Poslední příkaz přidá tento nový prvek Book k poskytovateli dat v souboru *zdrojový kód L2DBForm. XAML*. V důsledku toho bude dynamická vazba dat automaticky aktualizovat uživatelské rozhraní touto novou položkou; není vyžadován žádný další kód zadaný uživatelem.

## <a name="onremove-event-handler"></a>Rutina události při odebrání

Obslužná rutina `OnRemove` je složitější než `OnAddBook` obslužná rutina ze dvou důvodů. Nejprve, protože nezpracovaný kód XML obsahuje zachované prázdné znaky, musí být také z položky knihy odebrány newlines odpovídajícího kódu. S tím, jak pohodlí, výběr, který byl na odstraněnou položku, se v seznamu obnoví na předchozí.

Základní práce odebrání vybrané položky knihy se ale provádí jenom dvěma příkazy:

- Nejprve se načte element Book přidružený k aktuálně vybrané položce v seznamu:

    ```csharp
    XElement selBook = (XElement)lbBooks.SelectedItem;
    ```

- Pak se tento element odstraní od poskytovatele dat:

    ```csharp
    selBook.Remove();
    ```

Dynamická vazba dat znovu zajišťuje, že se uživatelské rozhraní programu automaticky aktualizuje.

## <a name="example"></a>Příklad

### <a name="code"></a>Kód

```csharp
using System;
using System.Linq;
using System.Collections;
using System.Collections.Generic;
using System.Diagnostics;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Input;
using System.Xml;
using System.Xml.Linq;

namespace LinqToXmlDataBinding {
    /// <summary>
    /// Interaction logic for L2XDBForm.xaml
    /// </summary>

    public partial class L2XDBForm : System.Windows.Window
    {
        XNamespace mybooks = "http://www.mybooks.com";
        XElement bookList;

        public L2XDBForm()
        {
            InitializeComponent();
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
        }

        void OnRemoveBook(object sender, EventArgs e)
        {
            int index = lbBooks.SelectedIndex;
            if (index < 0) return;

            XElement selBook = (XElement)lbBooks.SelectedItem;
            //Get next node before removing element.
            XNode nextNode = selBook.NextNode;
            selBook.Remove();

            //Remove any matching newline node.
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))
            { nextNode.Remove(); }

            //Set selected item.
            if (lbBooks.Items.Count > 0)
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }
        }

        void OnAddBook(object sender, EventArgs e)
        {
            if (String.IsNullOrEmpty(tbAddID.Text) ||
                String.IsNullOrEmpty(tbAddValue.Text))
            {
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");
                return;
            }
            XElement newBook = new XElement(
                                mybooks + "book",
                                new XAttribute("id", tbAddID.Text),
                                tbAddValue.Text);
            bookList.Add("  ", newBook, "\r\n");
        }
    }
}
```

### <a name="comments"></a>Komentáře

Související zdroj XAML pro tyto obslužné rutiny naleznete v tématu [zdrojový kód zdrojový kód L2DBForm. XAML](l2dbform-xaml-source-code.md).

## <a name="see-also"></a>Viz také:

- [Návod: příklad příkladu LinqToXmlDataBinding](linq-to-xml-data-binding-sample.md)
- [Zdrojový kód L2DBForm.xaml](l2dbform-xaml-source-code.md)
