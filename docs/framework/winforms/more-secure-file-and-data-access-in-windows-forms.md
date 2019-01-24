---
title: Více zabezpečený přístup k souborům a datům ve Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [Windows Forms], file access
- registry [Windows Forms]
- data access [Windows Forms]
- database access (Windows Forms security)
- data [Windows Forms], secure access
- file access [Windows Forms]
- security [Windows Forms], data access
ms.assetid: 3cd3e55b-2f5e-40dd-835d-f50f7ce08967
ms.openlocfilehash: 55e10a929be9c76bd8b33771945cf84f6228980f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679315"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Více zabezpečený přístup k souborům a datům ve Windows Forms
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Používá oprávnění k ochraně prostředkům a datům. Pokud vaše aplikace může číst nebo zapisovat data závisí na oprávněních udělených aplikaci. Když aplikace běží v prostředí částečným vztahem důvěryhodnosti, možná nebudete mít přístup k datům nebo budete muset změnit způsob, jak přistupovat k datům.  
  
 Pokud narazíte na omezení zabezpečení, máte dvě možnosti: uplatnit oprávnění (za předpokladu, že bylo uděleno pro vaši aplikaci) nebo verze operačního systému funkce napsané pro práci v částečném vztahu důvěryhodnosti. Následující části popisují, jak pracovat s souboru, database a přístup k registru z aplikací, které jsou spuštěny v prostředí s částečnou důvěryhodností.  
  
> [!NOTE]
>  Ve výchozím nastavení nástroje, které generují [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] nasazení ve výchozím nastavení tato nasazení žádající plné důvěryhodnosti z počítače, na kterých se používají. Pokud chcete využít výhod vyššího zabezpečení spouštění v částečném vztahu důvěryhodnosti, je nutné změnit toto výchozí nastavení v sadě Visual Studio nebo jeden z [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] nástroje (Mage.exe nebo MageUI.exe). Další informace o Windows Forms – zabezpečení a o tom, jak určit, příslušné úrovně důvěryhodnosti pro vaši aplikaci najdete v tématu [Přehled zabezpečení ve Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md).  
  
## <a name="file-access"></a>Přístup k souborům  
 <xref:System.Security.Permissions.FileIOPermission> Třídy ovládacích prvků přístupu souborů a složek v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Ve výchozím nastavení, systém zabezpečení nejsou udělena <xref:System.Security.Permissions.FileIOPermission> do prostředí částečným vztahem důvěryhodnosti, jako je místní intranet a Internet zóny. Aplikace, která vyžaduje přístup k souborům lze však i nadále fungovat v těchto prostředích je-li upravit návrh aplikace nebo použít různé metody pro přístup k souborům. Ve výchozím nastavení zóny místního intranetu je uděleno právo mít stejný přístup k serveru a stejný přístup adresáře pro připojení zpět k původnímu serveru a číst z jeho instalačního adresáře. Ve výchozím nastavení zóně Internet, je pouze uděleno právo na zpětné připojení k původnímu serveru.  
  
### <a name="user-specified-files"></a>Soubory zadané uživatelem  
 Jeden ze způsobů, jak zacházet s nemají přístup k souborům oprávnění je vyzvat uživatele k zadání určitých informací o souboru s použitím <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog> třídy. Tato interakce uživatele pomáhá poskytovat některé záruku, že aplikace nelze speciálně načíst soukromé soubory nebo přepsat důležitých souborů. <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> a <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody poskytují přístup čtení a zápis souboru otevřením souboru datového proudu souboru, který uživatel zadal. Metody také pomáhají chránit uživatele souboru zakódováním cestě k souboru.  
  
> [!NOTE]
>  Tato oprávnění se liší v závislosti na tom, zda je vaše aplikace v zóně Internet nebo intranet. Internetové zóně aplikace lze použít pouze <xref:System.Windows.Forms.OpenFileDialog>, že intranetové aplikace mít stejně neomezený souboru dialogové okno oprávnění.  
  
 <xref:System.Security.Permissions.FileDialogPermission> Třída určuje, jaký typ dialogového okna souboru může vaše aplikace použít. Následující tabulka uvádí hodnota musí mít použití každé <xref:System.Windows.Forms.FileDialog> třídy.  
  
|Třída|Hodnota požadovaný přístup|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
>  Konkrétní oprávnění není požadována až <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> skutečně volání metody.  
  
 Oprávnění k zobrazení dialogového okna souboru neuděluje vaše aplikace úplné přístup do všech členů <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, a <xref:System.Windows.Forms.SaveFileDialog> třídy. Konkrétní oprávnění, které je potřeba volat každou metodu, najdete v tématu referenční téma pro danou metodu v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] třídy dokumentaci ke knihovně.  
  
 Následující příklad kódu používá <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metody k otevření souboru zadaného uživatelem do <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. V příkladu vyžaduje <xref:System.Security.Permissions.FileDialogPermission> a přidružené <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> hodnota výčtu. Tento příklad ukazuje, jak zpracovat <xref:System.Security.SecurityException> k určení, zda uložit funkce by mělo být zakázáno. Tento příklad vyžaduje, aby vaše <xref:System.Windows.Forms.Form> má <xref:System.Windows.Forms.Button> ovládací prvek s názvem `ButtonOpen`a <xref:System.Windows.Forms.RichTextBox> ovládací prvek s názvem `RtfBoxMain`.  
  
> [!NOTE]
>  Programovou logiku pro uložení není funkce ukazuje příklad.  
  
```vb  
Private Sub ButtonOpen_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles ButtonOpen.Click   
  
    Dim editingFileName as String = ""  
    Dim saveAllowed As Boolean = True  
  
    ' Displays the OpenFileDialog.  
    If (OpenFileDialog1.ShowDialog() = DialogResult.OK) Then  
        Dim userStream as System.IO.Stream  
        Try   
            ' Opens the file stream for the file selected by the user.  
            userStream =OpenFileDialog1.OpenFile()   
            Me.RtfBoxMain.LoadFile(userStream, _  
                RichTextBoxStreamType.PlainText)  
        Finally  
            userStream.Close()  
        End Try  
  
        ' Tries to get the file name selected by the user.  
        ' Failure means that the application does not have  
        ' unrestricted permission to the file.  
        Try   
            editingFileName = OpenFileDialog1.FileName  
        Catch ex As Exception  
            If TypeOf ex Is System.Security.SecurityException Then   
                ' The application does not have unrestricted permission   
                ' to the file so the save feature will be disabled.  
                saveAllowed = False   
            Else   
                Throw ex  
            End If  
        End Try  
    End If  
End Sub  
```  
  
```csharp  
private void ButtonOpen_Click(object sender, System.EventArgs e)   
{  
    String editingFileName = "";  
    Boolean saveAllowed = true;  
  
    // Displays the OpenFileDialog.  
    if (openFileDialog1.ShowDialog() == DialogResult.OK)   
    {  
        // Opens the file stream for the file selected by the user.  
        using (System.IO.Stream userStream = openFileDialog1.OpenFile())   
        {  
            this.RtfBoxMain.LoadFile(userStream,  
                RichTextBoxStreamType.PlainText);  
            userStream.Close();  
        }  
  
        // Tries to get the file name selected by the user.  
        // Failure means that the application does not have  
        // unrestricted permission to the file.  
        try   
        {  
            editingFileName = openFileDialog1.FileName;  
        }   
        catch (Exception ex)   
        {  
            if (ex is System.Security.SecurityException)   
            {  
                // The application does not have unrestricted permission   
                // to the file so the save feature will be disabled.  
                saveAllowed = false;   
            }   
            else   
            {  
                throw ex;  
            }  
        }  
    }  
}  
```  
  
> [!NOTE]
>  V jazyce Visual C#, ujistěte se, že přidáte kód pro povolení obslužné rutiny události. S použitím kódu z předchozího příkladu, následující kód ukazuje, jak povolit obslužné rutiny události.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>Další soubory  
 Někdy můžete potřebovat pro čtení nebo zápis do souborů, že uživatel není zadán, například když musíte zachovat nastavení aplikace. V místní intranet a Internet zóny vaše aplikace nebude mít oprávnění k ukládání dat do místního souboru. Ale aplikace bude moct ukládání dat v izolovaném úložišti. Izolované úložiště je abstraktní datové přihrádky (nikoli specifickým umístěním úložiště), který obsahuje jeden nebo více souborů izolovaného úložiště nazývají "úložiště", které obsahují umístění skutečného adresáře, kde jsou uložená data. Soubor přístupová oprávnění jako <xref:System.Security.Permissions.FileIOPermission> nejsou povinné; místo toho <xref:System.Security.Permissions.IsolatedStoragePermission> třídy řídí oprávnění pro izolované úložiště. Ve výchozím nastavení aplikace, které jsou spuštěny v místním intranetu a Internetu zóny může ukládat data pomocí izolované úložiště. nastavení, jako je disková kvóta se však může lišit. Další informace o izolovaného úložiště naleznete v tématu [izolovaného úložiště](../../../docs/standard/io/isolated-storage.md).  
  
 Následující příklad používá k zápisu dat do souboru, který je umístěn v úložišti izolovaného úložiště. V příkladu vyžaduje <xref:System.Security.Permissions.IsolatedStorageFilePermission> a <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> hodnota výčtu. Příklad ukazuje, čtení a zápis do určité hodnoty vlastností <xref:System.Windows.Forms.Button> ovládacího prvku do souboru v izolovaném úložišti. `Read` Funkce by byla volána po spuštění aplikace a `Write` funkce by byla volána před ukončením aplikace. V příkladu vyžaduje, aby `Read` a `Write` funkce existovat jako členy <xref:System.Windows.Forms.Form> , která obsahuje <xref:System.Windows.Forms.Button> ovládací prvek s názvem `MainButton`.  
  
```vb  
' Reads the button options from the isolated storage. Uses Default values   
' for the button if the options file does not exist.  
Public Sub Read()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try  
        ' Checks to see if the options.txt file exists.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
  
            ' Opens the file because it exists.  
            Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
                 (filename, IO.FileMode.Open,isoStore)  
            Dim reader as System.IO.StreamReader  
            Try   
                reader = new System.IO.StreamReader(isos)  
  
                ' Reads the values stored.  
                Dim converter As System.ComponentModel.TypeConverter  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Color))  
  
                Me.MainButton.BackColor = _   
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
                me.MainButton.ForeColor = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Font))  
                me.MainButton.Font = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Font)  
  
            Catch ex As Exception  
                Debug.WriteLine("Cannot read options " + _  
                    ex.ToString())  
            Finally  
                reader.Close()  
            End Try  
        End If  
  
    Catch ex As Exception  
        Debug.WriteLine("Cannot read options " + ex.ToString())  
    End Try  
End Sub  
  
' Writes the button options to the isolated storage.  
Public Sub Write()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try   
        ' Checks if the file exists, and if it does, tries to delete it.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
            isoStore.DeleteFile(filename)  
        End If  
    Catch ex As Exception  
        Debug.WriteLine("Cannot delete file " + ex.ToString())  
    End Try  
  
    ' Creates the options.txt file and writes the button options to it.  
    Dim writer as System.IO.StreamWriter  
    Try   
        Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
             (filename, IO.FileMode.CreateNew, isoStore)  
  
        writer = New System.IO.StreamWriter(isos)  
        Dim converter As System.ComponentModel.TypeConverter  
  
        converter = System.ComponentModel.TypeDescriptor.GetConverter _   
           (GetType(Color))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.BackColor))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.ForeColor))  
  
        converter = System.ComponentModel TypeDescriptor.GetConverter _   
           (GetType(Font))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.Font))  
  
    Catch ex as Exception  
        Debug.WriteLine("Cannot write options " + ex.ToString())  
  
    Finally  
        writer.Close()  
    End Try  
End Sub  
```  
  
```csharp  
// Reads the button options from the isolated storage. Uses default values   
// for the button if the options file does not exist.  
public void Read()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try  
    {  
        // Checks to see if the options.txt file exists.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            // Opens the file because it exists.  
            System.IO.IsolatedStorage.IsolatedStorageFileStream isos =   
                new System.IO.IsolatedStorage.IsolatedStorageFileStream  
                    (filename, System.IO.FileMode.Open,isoStore);  
            System.IO.StreamReader reader = null;  
            try   
            {  
                reader = new System.IO.StreamReader(isos);  
  
                // Reads the values stored.  
                TypeConverter converter ;  
                converter = TypeDescriptor.GetConverter(typeof(Color));  
  
                this.MainButton.BackColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
                this.MainButton.ForeColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
  
                converter = TypeDescriptor.GetConverter(typeof(Font));  
                this.MainButton.Font =   
                  (Font)(converter.ConvertFromString(reader.ReadLine()));  
            }  
            catch (Exception ex)  
            {   
                System.Diagnostics.Debug.WriteLine  
                     ("Cannot read options " + ex.ToString());  
            }  
            finally  
            {  
                reader.Close();  
            }  
        }  
    }   
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot read options " + ex.ToString());  
    }  
}  
  
// Writes the button options to the isolated storage.  
public void Write()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try   
    {  
        // Checks if the file exists and, if it does, tries to delete it.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            isoStore.DeleteFile(filename);  
        }  
    }  
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot delete file " + ex.ToString());  
    }  
  
    // Creates the options file and writes the button options to it.  
    System.IO.StreamWriter writer = null;  
    try   
    {  
        System.IO.IsolatedStorage.IsolatedStorageFileStream isos = new   
            System.IO.IsolatedStorage.IsolatedStorageFileStream(filename,   
            System.IO.FileMode.CreateNew,isoStore);  
  
        writer = new System.IO.StreamWriter(isos);  
        TypeConverter converter ;  
  
        converter = TypeDescriptor.GetConverter(typeof(Color));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.BackColor));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.ForeColor));  
  
        converter = TypeDescriptor.GetConverter(typeof(Font));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.Font));  
  
    }  
    catch (Exception ex)  
    {   
        System.Diagnostics.Debug.WriteLine  
           ("Cannot write options " + ex.ToString());  
    }  
    finally  
    {  
        writer.Close();  
    }  
}  
```  
  
## <a name="database-access"></a>Přístup k databázi  
 Oprávnění potřebná pro přístup k databázi se liší v závislosti na poskytovateli databáze; jenom aplikace, které jsou spuštěny s příslušnými oprávněními ale může přístup k databázi prostřednictvím datového připojení. Další informace o oprávněních, které jsou nutné pro přístup k databázi, naleznete v tématu [zabezpečení přístupu kódu a ADO.NET](../../../docs/framework/data/adonet/code-access-security.md).  
  
 Pokud databáze nemůžete použít přímo, protože chcete, aby aplikace na spouštění v částečném vztahu důvěryhodnosti, můžete použít webovou službu, jako alternativu znamená, že přístup k datům. Webové služby je software, který můžete programově přistupovat přes síť. U webových služeb mohou aplikace sdílet data napříč zónami skupiny kódu. Ve výchozím nastavení aplikace v místním intranetu a Internetu zóny jsou udělena oprávnění k přístupu k jejich lokality původ, odkud můžou k volání webové služby hostované na stejném serveru. Další informace najdete v části [webové služby v technologii ASP.NET AJAX](https://msdn.microsoft.com/library/8290e543-7eff-47a4-aace-681f3c07229b) nebo [Windows Communication Foundation](https://msdn.microsoft.com/library/ms735119.aspx).  
  
## <a name="registry-access"></a>Přístup k registru  
 <xref:System.Security.Permissions.RegistryPermission> Třídy řídí přístup k registru operačního systému. Ve výchozím nastavení můžete pouze aplikace, které jsou spuštěné místně přístup k registru.  <xref:System.Security.Permissions.RegistryPermission> uděluje jenom aplikace právo zkuste přístup k registru; to nezaručuje, že přístup bude úspěšné, protože operační systém stále vynucuje zabezpečení v registru.  
  
 Protože nelze získat přístup k registru v částečném vztahu důvěryhodnosti, budete muset najít jiné metody ukládání dat. Při ukládání nastavení aplikace používání izolovaného úložiště namísto registru. Izolované úložiště lze také ukládat další soubory specifické pro aplikaci. Můžete také ukládat informace o globální aplikace o server nebo server původu, protože ve výchozím nastavení aplikace jsou udělena oprávnění k přístupu k původnímu serveru.  
  
## <a name="see-also"></a>Viz také:
- [Zabezpečenější tisk ve Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)
- [Dodatečné informace o zabezpečení ve Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)
- [Přehled zabezpečení ve Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)
- [Windows Forms – zabezpečení](../../../docs/framework/winforms/windows-forms-security.md)
- [Mage.exe (Manifest Generation and Editing Tool)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
