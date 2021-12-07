Sub edit_charts()
        Dim sh As Worksheet, i As Long
        For Each sh In Worksheets
            If sh.ChartObjects.Count > 0 Then
                For i = 1 To sh.ChartObjects.Count
                    If sh.ChartObjects(i).Chart.HasLegend Then
                        sh.ChartObjects(i).Chart.Legend.Font.Size = 11
                        sh.ChartObjects(i).Chart.Legend.Font.Bold = True
                    End If

                    sh.ChartObjects(i).Chart.ChartArea.Border.Color = 0 ' 0 = schwarz
                    sh.ChartObjects(i).Chart.ChartArea.Border.Weight = XlBorderWeight.xlThin

                    For Each Achse In sh.ChartObjects(i).Chart.Axes()
                        Achse.TickLabels.Font.Size = 11
                        Achse.TickLabels.Font.Bold = True
                        If Achse.HasTitle Then
                            Achse.AxisTitle.Font.Size = 11
                            Achse.AxisTitle.Font.Bold = True
                        End If
                    Next

                Next i
            End If
        Next sh
    End Sub
