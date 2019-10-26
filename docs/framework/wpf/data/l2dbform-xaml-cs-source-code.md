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
# <a name="l2dbformxamlcs-source-code"></a><span data-ttu-id="c9b14-102">Zdrojový kód L2DBForm.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="c9b14-102">L2DBForm.xaml.cs source code</span></span>

<span data-ttu-id="c9b14-103">Tato stránka obsahuje obsah a popis C# zdrojového kódu v souboru *L2DBForm.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="c9b14-103">This page contains the contents and description of the C# source code in the file *L2DBForm.xaml.cs*.</span></span> <span data-ttu-id="c9b14-104">Částečná třída L2XDBForm obsažená v tomto souboru může být rozdělena do tří logických částí: datové členy a `OnRemove` a `OnAddBook` kliknutí na tlačítko obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="c9b14-104">The L2XDBForm partial class contained in this file can be divided into three logical sections: data members and the `OnRemove` and `OnAddBook` button click event handlers.</span></span>

## <a name="data-members"></a><span data-ttu-id="c9b14-105">Datové členy</span><span class="sxs-lookup"><span data-stu-id="c9b14-105">Data members</span></span>

<span data-ttu-id="c9b14-106">K přidružení této třídy k prostředkům okna použitým v souboru *zdrojový kód L2DBForm. XAML*se používají dva soukromé datové členy.</span><span class="sxs-lookup"><span data-stu-id="c9b14-106">Two private data members are used to associate this class to the window resources used in *L2DBForm.xaml*.</span></span>

- <span data-ttu-id="c9b14-107">Proměnná oboru názvů `myBooks` se inicializuje na `"http://www.mybooks.com"`.</span><span class="sxs-lookup"><span data-stu-id="c9b14-107">The namespace variable `myBooks` is initialized to `"http://www.mybooks.com"`.</span></span>

- <span data-ttu-id="c9b14-108">Členský `bookList` je inicializován v konstruktoru do řetězce CDATA v souboru *zdrojový kód L2DBForm. XAML* s následujícím řádkem:</span><span class="sxs-lookup"><span data-stu-id="c9b14-108">The member `bookList` is initialized in the constructor to the CDATA string in *L2DBForm.xaml* with the following line:</span></span>

    ```csharp
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
    ```

## <a name="onaddbook-event-handler"></a><span data-ttu-id="c9b14-109">Obslužná rutina události OnAddBook</span><span class="sxs-lookup"><span data-stu-id="c9b14-109">OnAddBook event handler</span></span>

<span data-ttu-id="c9b14-110">Tato metoda obsahuje následující tři příkazy:</span><span class="sxs-lookup"><span data-stu-id="c9b14-110">This method contains the following three statements:</span></span>

- <span data-ttu-id="c9b14-111">První podmíněný příkaz se používá pro ověření vstupu.</span><span class="sxs-lookup"><span data-stu-id="c9b14-111">The first conditional statement is used for input validation.</span></span>

- <span data-ttu-id="c9b14-112">Druhý příkaz vytvoří nový <xref:System.Xml.Linq.XElement> z hodnot řetězce, které uživatel zadal v oddílu **Přidat novou knihu** uživatelského rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="c9b14-112">The second statement creates a new <xref:System.Xml.Linq.XElement> from the string values the user entered in the **Add New Book** user interface (UI) section.</span></span>

- <span data-ttu-id="c9b14-113">Poslední příkaz přidá tento nový prvek Book k poskytovateli dat v souboru *zdrojový kód L2DBForm. XAML*.</span><span class="sxs-lookup"><span data-stu-id="c9b14-113">The last statement adds this new book element to the data provider in *L2DBForm.xaml*.</span></span> <span data-ttu-id="c9b14-114">V důsledku toho bude dynamická vazba dat automaticky aktualizovat uživatelské rozhraní touto novou položkou; není vyžadován žádný další kód zadaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="c9b14-114">Consequently, dynamic data binding will automatically update the UI with this new item; no extra user-supplied code is required.</span></span>

## <a name="onremove-event-handler"></a><span data-ttu-id="c9b14-115">Rutina události při odebrání</span><span class="sxs-lookup"><span data-stu-id="c9b14-115">OnRemove event handler</span></span>

<span data-ttu-id="c9b14-116">Obslužná rutina `OnRemove` je složitější než `OnAddBook` obslužná rutina ze dvou důvodů.</span><span class="sxs-lookup"><span data-stu-id="c9b14-116">The `OnRemove` handler is more complicated than the `OnAddBook` handler for two reasons.</span></span> <span data-ttu-id="c9b14-117">Nejprve, protože nezpracovaný kód XML obsahuje zachované prázdné znaky, musí být také z položky knihy odebrány newlines odpovídajícího kódu.</span><span class="sxs-lookup"><span data-stu-id="c9b14-117">First, because the raw XML contains preserved white space, matching newlines must also be removed with the book entry.</span></span> <span data-ttu-id="c9b14-118">S tím, jak pohodlí, výběr, který byl na odstraněnou položku, se v seznamu obnoví na předchozí.</span><span class="sxs-lookup"><span data-stu-id="c9b14-118">Second, as a convenience, the selection, which was on the deleted item, is reset to the previous one in the list.</span></span>

<span data-ttu-id="c9b14-119">Základní práce odebrání vybrané položky knihy se ale provádí jenom dvěma příkazy:</span><span class="sxs-lookup"><span data-stu-id="c9b14-119">However, the core work of removing the selected book item is accomplished by only two statements:</span></span>

- <span data-ttu-id="c9b14-120">Nejprve se načte element Book přidružený k aktuálně vybrané položce v seznamu:</span><span class="sxs-lookup"><span data-stu-id="c9b14-120">First, the book element associated with the currently selected item in the list box is retrieved:</span></span>

    ```csharp
    XElement selBook = (XElement)lbBooks.SelectedItem;
    ```

- <span data-ttu-id="c9b14-121">Pak se tento element odstraní od poskytovatele dat:</span><span class="sxs-lookup"><span data-stu-id="c9b14-121">Then, this element is deleted from the data provider:</span></span>

    ```csharp
    selBook.Remove();
    ```

<span data-ttu-id="c9b14-122">Dynamická vazba dat znovu zajišťuje, že se uživatelské rozhraní programu automaticky aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="c9b14-122">Again, dynamic data binding assures that the program's UI is automatically updated.</span></span>

## <a name="example"></a><span data-ttu-id="c9b14-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9b14-123">Example</span></span>

### <a name="code"></a><span data-ttu-id="c9b14-124">Kód</span><span class="sxs-lookup"><span data-stu-id="c9b14-124">Code</span></span>

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

### <a name="comments"></a><span data-ttu-id="c9b14-125">Komentáře</span><span class="sxs-lookup"><span data-stu-id="c9b14-125">Comments</span></span>

<span data-ttu-id="c9b14-126">Související zdroj XAML pro tyto obslužné rutiny naleznete v tématu [zdrojový kód zdrojový kód L2DBForm. XAML](l2dbform-xaml-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="c9b14-126">For the associated XAML source for these handlers, see [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9b14-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9b14-127">See also</span></span>

- [<span data-ttu-id="c9b14-128">Návod: příklad příkladu LinqToXmlDataBinding</span><span class="sxs-lookup"><span data-stu-id="c9b14-128">Walkthrough: LinqToXmlDataBinding example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="c9b14-129">Zdrojový kód L2DBForm.xaml</span><span class="sxs-lookup"><span data-stu-id="c9b14-129">L2DBForm.xaml source code</span></span>](l2dbform-xaml-source-code.md)
